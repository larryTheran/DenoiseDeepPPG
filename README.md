# Denoise PPG Using Deep Learning Networks

DenoiseDeepPPG is one of the result in the project of Center of Advance Wearable technologies (CWAT). This especified part is foccuses on removing the noise artifact generated during the measurement of a photoplethysmography (PPG) signal. The signal used was sintetically generate using the alogorithm propouse by (). For the denoiser we used layers of a fully convolutional network comprising 16 convolutional layers. The first 15 convolutional layers are groups of 3 layers, repeated 5 times, with filter widths of 9, 5, and 9, and number of filters of 18, 30 and 8, respectively. The last convolutional layer has a filter width of 129 and 1 filter. For DenoiseDeepPPG, the code from Matlab has been adapted to work with PPG signal generated, the code has been adapted from https://www.mathworks.com/help/deeplearning/ug/denoise-speech-using-deep-learning-networks.html

This project is capable to remove high level of noise from a PPG signal used in biomedical aplications.

Matlab 2021 have been used in this project.

# Create PPG Synthetic Dataset

To create the dataset we use the work published by Qunfeng Tang et all ('PPGSynth: An Innovative Toolbox for Synthesizing Regular and Irregular Photoplethysmography Waveforms'), this work is based on the photoplethysmogram generation using two Gaussian functions (https://www.nature.com/articles/s41598-020-69076-x). Base on that we modified the original code to generate the same signal with a gaussian noise adeed, in order to be used as an imput for our denoiser.



![Original_PPG](https://user-images.githubusercontent.com/55849820/117089701-3a17d380-ad24-11eb-82da-d07a28ff9348.jpg)


# Generate network image input data from PPG signal



# Network Arquitecture

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
 
