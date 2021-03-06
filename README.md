
# Denoise PPG Using Deep Learning Networks

DenoiseDeepPPG is one of the result in the project of Center of Advance Wearable technologies (CWAT). This especified part is foccuses on removing the noise artifact generated during the measurement of a photoplethysmography (PPG) signal. The signal used was sintetically generate using the alogorithm propouse by (). For the denoiser we used layers of a fully convolutional network comprising 16 convolutional layers. The first 15 convolutional layers are groups of 3 layers, repeated 5 times, with filter widths of 9, 5, and 9, and number of filters of 18, 30 and 8, respectively. The last convolutional layer has a filter width of 129 and 1 filter. For DenoiseDeepPPG, the code from Matlab has been adapted to work with PPG signal generated, the code has been adapted from https://www.mathworks.com/help/deeplearning/ug/denoise-speech-using-deep-learning-networks.html

This project is capable to remove high level of noise from a PPG signal used in biomedical aplications.

Matlab 2021 have been used in this project.

# Create PPG Synthetic Dataset

To create the dataset we use the work published by Qunfeng Tang et all ('PPGSynth: An Innovative Toolbox for Synthesizing Regular and Irregular Photoplethysmography Waveforms'), this work is based on the photoplethysmogram generation using two Gaussian functions (https://www.nature.com/articles/s41598-020-69076-x). Base on that we modified the original code to generate the same signal with a gaussian noise adeed, in order to be used as an imput for our denoiser.


![Original_PPG](https://user-images.githubusercontent.com/55849820/117089701-3a17d380-ad24-11eb-82da-d07a28ff9348.jpg)


# Generate network image input data from PPG signal



# Network Arquitecture

The input of the CNN are the spectrograms of the PPG signal as shown in the figure 2, the input layer receive the image od size 129x8, where 8 is the number of partition that has been concatenate after the application of the Short Time Fourier Transform (STFT). The output is an spectrogram with size 129x8.

layers = [imageInputLayer([NumFeatures,NumSegments])
          convolution2dLayer([9 8],18,"Stride",[1 100],"Padding","same")
          batchNormalizationLayer
          reluLayer
          
          repmat(...
          [convolution2dLayer([5 1],30,"Stride",[1 100],"Padding","same")
          batchNormalizationLayer
          reluLayer
          
          convolution2dLayer([9 1],8,"Stride",[1 100],"Padding","same")
          batchNormalizationLayer
          reluLayer
          
          convolution2dLayer([9 1],18,"Stride",[1 100],"Padding","same")
          batchNormalizationLayer
          reluLayer], 4,1) % repeat this sequence 4 times
          
          convolution2dLayer([5 1],30,"Stride",[1 100],"Padding","same")
          batchNormalizationLayer
          reluLayer
          
          convolution2dLayer([9 1],8,"Stride",[1 100],"Padding","same")
          batchNormalizationLayer
          reluLayer
          
          convolution2dLayer([129 1],1,"Stride",[1 100],"Padding","same")
          
          regressionLayer
          ]
 
 The input of the CNN are the spectrograms of the PPG signal, the input layer receives the image od size 129x8, where 8 is the number of partitions that has been concatenate after the application of the Short Time Fourier Transform (STFT). The output is a spectrogram with size 129x8.
 
 # Spectrogram for the PPG and noise PPG signals.         


<img width="1479" alt="Screen Shot 2021-05-04 at 10 26 15 PM" src="https://user-images.githubusercontent.com/55849820/117090939-c1b31180-ad27-11eb-8001-efaf6af0a8ed.png">
 
 In this case the noise PPG spectrogram is used as a predictor and the clean PPG spectrogram is used as a target
 
 <img width="1036" alt="Screen Shot 2021-05-04 at 10 30 18 PM" src="https://user-images.githubusercontent.com/55849820/117091115-50c02980-ad28-11eb-96f9-f5d31fbccffc.png">
 
 <img width="990" alt="Screen Shot 2021-05-04 at 10 30 53 PM" src="https://user-images.githubusercontent.com/55849820/117091152-66cdea00-ad28-11eb-81b9-5947d9df9d82.png">


 
