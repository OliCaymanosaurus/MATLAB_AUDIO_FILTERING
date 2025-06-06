filename = "Project\3 Minute Beethoven, Symphony No. 5.  🎼🎶🎵.wav"; %song input (we need to change the song because it is too basic because I was going to do it for a different project.

%read audio file
[audio, fs] = audioread("Project/Songs/3 Minute Beethoven, Symphony No. 5.  🎼🎶🎵.wav");


t = (0:length(audio)-1)/fs ;%seconds of audio file

%plotting audio file
figure;

plot(t,audio) ;
title("Audio File");
xlabel("Time(seconds)");
ylabel("Amplitude");

%Power Spectrum of Audio
[p,f] = pspectrum(audio,fs);

%Convert Power to decibel(dB) using pow2db function
p_dB = pow2db(p);




%Adding Bass (Amplifying Low Frequencies) through lowpass filter
audio_bass = lowpass(audio,200,fs,'Steepness',0.85,'StopbandAttenuation',60);


%Power Spectrum of Bass Boosted Audio
[pb,fb] = pspectrum(audio_bass,fs);
%Convert Power to dB
pb_dB = pow2db(pb);

figure;
plot(f, p_dB, "Color", 'r', "DisplayName",'Original' );  
hold on
plot(fb, pb_dB,"Color", "b", "DisplayName", 'Bass Boosted')
legend show;
grid on;
xlabel('Frequency (Hz)');
ylabel('Power Spectrum (dB)');
title('Power Spectrum of Audio Signal - with Bass');
hold off
NewBassFile = 'audio_bass.wav';
audiowrite(NewBassFile, audio_bass, fs)


%Adding Treble (Amplifying High Frequencies) 
audio_treble = highpass(audio,2000,fs,'Steepness',0.85,'StopbandAttenuation',60);

%Power Spectrum of Treble Boosted Audio
[pt,ft] = pspectrum(audio_treble,fs);

%Cover Power to dB
pt_dB = pow2db(pt);

%Graph 
figure;
plot(f, p_dB, "Color", 'r', "DisplayName",'Original' );  
hold on
plot(ft, pt_dB,"Color", "g", "DisplayName", 'Treble Boosted')
legend show;
grid on;
xlabel('Frequency (Hz)');
ylabel('Power Spectrum (dB)');
title('Power Spectrum of Audio Signal - with Treble');
hold off
NewTrebleFile = 'audio_treble.wav';
audiowrite(NewTrebleFile, audio_treble, fs)

%Midrange frequencies 
audio_mid = bandpass(audio,[6000 12000],fs,'Steepness',0.85,'StopbandAttenuation',60);
[gluc,pp] = pspectrum(audio_mid,fs);
gluc_dB = pow2db(gluc);
figure;
plot(f, p_dB, "Color", 'r', "DisplayName",'Original' );  
hold on
plot(pp, gluc_dB,"Color", "g", "DisplayName", 'Mid-Range Boost')
legend show;
grid on;
xlabel('Frequency (Hz)');
ylabel('Power Spectrum (dB)');
title('Power Spectrum of Audio Signal');
hold off
NewMidFile = 'audio_mid.wav';
audiowrite(NewMidFile, audio_mid, fs)

plot(f, p_dB, "Color", 'r', "DisplayName",'Original' );  
hold on
plot(fb, pb_dB,"Color", "b", "DisplayName", 'Bass Boosted')
plot(ft, pt_dB,"Color", "g", "DisplayName", 'Treble Boosted')
legend show;
grid on;
xlabel('Frequency (Hz)');
ylabel('Power Spectrum (dB)');
title('Power Spectrum of Audio Signal - with Bass');
hold off

