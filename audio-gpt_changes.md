> Path to T2A (text to audio) class definition: 
>> audio-chatgpt.py
>>> Updated sampling rates from 16000 to 44100 ***
>>> Updated config file to increase audio quality. See txt2audio_args.yaml ref below ***
>>> Updated ddim_steps from 100 to 400 to smoothen audio, reduce noise ***
>>> Increased the scale from 1.5 to 6 to sharpen the output ***
>>>: updated sampling rate in config file to 96000 from 44100



> Path to I2A (image to audio) class definition: 
>> audio-chatgpt.py 
>>> Updated sampling rates from 16000 to 44100 
>>> Updated config file to increase audio quality. See txt2audio_args.yaml ref below 
>>> Updated ddim_steps from 100 to 400 to smoothen audio, reduce noise 
>>> Increased the scale from 3 to 6 to sharpen the output 



> Path to TTS (text to speech) class definition: 
>> audio-chatgpt.py
>>> Updated sampling rates from 22050 to 44100 
>>> Added code to average out 3 inferences rather than just inferencing once. Could help improve quality, stability and reduce artifacts 



> Path to T2S (text to sing) class definition: 
>> audio-chatgpt.py
>>> Increased bit depth from 16 to 24 (pads to 32 bit int though). wav scaling changed from 32767 to 8388607



> Path to TTS_OOD () class definition: 
>> audio-chatgpt.py
>>> Increased bit depth from 16 to 24 (pads to 32 bit int though). wav scaling changed from 32767 to 8388607 
>>> Updated generspeech config file. see below



> Path to Inpaint class definition: 
>> audio-chatgpt.py 
>>> sampler config file was updated 
>>> updated sampling rate from 16000 to 44100 
>>> updated ddim_steps from 100 to 400 
>>> Added transforms 44100 method to increase usage from human speech to music and other audible sounds 



> Path to SoundDetection class definition: 
>> audio-chatgpt.py
>>> Increased sample rate from 32000 to 64000 
>>> Updated freq min: 50 --> 20, freq max: 14000 --> 20000 
>>> Increased window_size: 1024 --> 2048 for better freq resolution (more samples captured) 
>>> Decreased hop_size: 320 --> 256 for better time accuracy (more precise) 
>>> Increased mel_bins: 64 --> 128 for higher spectral resolution (more granularity, more detail captured) 



> Path to SoundExtraction class definition: 
>> audio-chatgpt.py
>>> Modified load_wav and save_wav definitions to increase sampling rate and bit depth
>>> See wav_io.py



> Path to Binaural class definition: 
>> audio-chatgpt.py 
>>>  : updating sr from 48000 to 96000
>>>  : changing warpnet_layers from 4 to 8 --> deeper model for higher quality
>>>  : changing warpnet_channels from 64 to 256 --> more channels to capture more audio detail
>>>  : updated rec_field from 1000 to 4800 to reduce artifacts and smoothen transitions



> Path to TargetSoundDetection class definition: 
>> audio-chatgpt.py
>>> updating MeL_ARGS values. n_mels from 64 --> 128, n_fft from 2048 --> 4096, hop_length multiplier from 20 --> 10, win_length multipler from 40 --> 60
>>> mel bins changes improves frequency resolution
>>> n_fft changes increases freq resolution
>>> smaller hop length increases number of frames captured, more audio detail captured
>>> larger windowns size improves spectrogram smoothness, better freq resolution
>>> updated sample rate from 22050 Hz to 44100



> Path to Speech_Enh_SS_SC (Speech Enhancement) class definition: 
>> audio-chatgpt.py
>>> slightly increased segment_size from 2.4 --> 4.0. Larger seg size improves continuity
>>> slightly decreased hop_size from 0.8 --> 0.5. smaller hop size smoothens transitions
>>> added a 2x multiplier to the recorded audio sample rate to potentially improve quality of separated speech



> Path to Speech_SS (Speech Separation) class definition: 
>> audio-chatgpt.py
>>> slightly increased segment_size from 2.4 --> 4.0. Larger seg size improves continuity
>>> slightly decreased hop_size from 0.8 --> 0.5. smaller hop size smoothens transitions
>>> added a 2x multiplier to the recorded audio sample rate to potentially improve quality of separated speech



> Path to infer_once definition:
>> NeuralSeq\inference\tts\base_tts_infer.py
>>> This is used in TTS, T2S, TTS_OOD, and GeneFace classes
>>> Updating to average out 10 inferences, which could remove randomness from speech creation


> Path to txt2audio_args.yaml 
>> text_to_audio\Make_An_Audio\configs\text_to_audio\txt2audio_args.yaml
>>> Increasing channel sizes from 4 to 16 
>>> downloaded paths for checkpoint models. They must be compatible with 16 channels or I will need to revert back to 4 
>>> increasing number of timesteps from 1 to 5, and increasing the timesteps from 1000 to 8000 --> Allows more room for the audio to denoise and remove artifacts, and enhance audio fidelity 
>>> Enabled EMA for more stable sampling  
>>> Increased warmup steps to smoothen learning transistion 


> Path to config.yml (called in T2A class --> method: select_best_audio) 
>> text_to_audio\Make_An_Audio\useful_ckpts\CLAP\config.yml 
>>> Changed sampling rate from 44100 to 96000 

> Path to generspeech.yaml (called in TTS OOD --> method: init)
>> NeuralSeq\modules\GenerSpeech\config\generspeech.yaml
>>> Increased sample rate from 16000 to 44100
>>> fmin from 80 to 50
>>> fmax from 7600 to 8200

> Path to extract_mel_spectrogram 
>> text_to_audio\Make_An_Audio\ldm\data\extract_mel_spectrogram.py 
>>> Added transforms 44100 method to increase usage from human speech to music and other audible sounds 
>>> Used in the audio inpainting class and 




> Path to wav_io.py (used for SoundExtraction)
>> sound_extraction\utils\wav_io.py
>>> Updating SR and max_length to 64000 from 32000
>>> Increased bit depth from 16 to 24 (pads to 32 bit int though). wav scaling changed from 32767 to 8388607

*** Looking to increase bit depth of sound files ***

Path to AudioEncoder class:
text_to_audio\Make_An_Audio --> wav_evaluation\models --> clap.py

Path to Upsample, Downsample, Encoder, and Decoder classes:
text to audio \ make an audio --> Idm  modules  diffusionmodels --> models.py

