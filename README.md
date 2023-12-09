# eog
% Generate or load a sample EOG signal (replace this with your actual data)
% For demonstration purposes, let's generate a sample EOG signal
fs = 1000;  % Sampling frequency (adjust as needed)
t = 0:1/fs:10;  % Time vector
eog_signal = sin(2*pi*0.1*t) + randn(size(t))*0.2;

% Plot the EOG signal
figure;
subplot(3,1,1);
plot(t, eog_signal);
title('EOG Signal');
xlabel('Time (s)');
ylabel('Amplitude');

% Use a threshold-based approach to detect eye movement artifacts
threshold = 0.5;  % Adjust as needed based on your signal characteristics
eog_artifacts = abs(eog_signal) > threshold;

% Plot detected eye movement artifacts
subplot(3,1,2);
plot(t, eog_signal);
hold on;
plot(t(eog_artifacts), eog_signal(eog_artifacts), 'r*');
title('Detected EOG Artifacts');
xlabel('Time (s)');
ylabel('Amplitude');

% Display the percentage of time with detected artifacts
artifact_percentage = sum(eog_artifacts) / length(eog_artifacts) * 100;
subplot(3,1,3);
text(0.5, 0.5, sprintf('Artifact Percentage: %.2f%%', artifact_percentage), 'FontSize', 12, 'HorizontalAlignment', 'center');
axis off;

% Adjust subplot spacing
subplot(3,1,1);
sgtitle('EOG Artifact Detection');

