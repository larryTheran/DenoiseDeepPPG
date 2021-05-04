# DenoiseDeepPPG

DenoiseDeepPPG is one of the result in the project of Center of Advance Wearable technologies (CWAT). This especified part is foccuses on removing the noise artifact generated during the measurement of a photoplethysmography (PPG) signal. The signal used was sintetically generate using the alogorithm propouse by (). For the denoiser we used the Convolutional Neural Network propoused in the work (), that combines 3 convolutional leyers. For DenoiseDeepPPG, the code from Matlab has been adapted to work with PPG signal generated, the code has been adapted from https://github.com/zzh8829/yolov3-tf2.

This project is capable to remove high level of noise from a PPG signal used in biomedical aplications.

Matlab 2021 have been used in this project.

# Network Arquitecture

layers = 
  1x59 Layer array with layers:

     1   'InputLayer'             Image Input           50x50x1 images
     2   'Conv1'                  Convolution           64 3x3x1 convolutions with stride [1  1] and padding [1  1  1  1]
     3   'ReLU1'                  ReLU                  ReLU
     4   'Conv2'                  Convolution           64 3x3x64 convolutions with stride [1  1] and padding [1  1  1  1]
     5   'BNorm2'                 Batch Normalization   Batch normalization with 64 channels
     6   'ReLU2'                  ReLU                  ReLU
     7   'Conv3'                  Convolution           64 3x3x64 convolutions with stride [1  1] and padding [1  1  1  1]
     8   'BNorm3'                 Batch Normalization   Batch normalization with 64 channels
     9   'ReLU3'                  ReLU                  ReLU
    10   'Conv4'                  Convolution           64 3x3x64 convolutions with stride [1  1] and padding [1  1  1  1]
    11   'BNorm4'                 Batch Normalization   Batch normalization with 64 channels
    12   'ReLU4'                  ReLU                  ReLU
    13   'Conv5'                  Convolution           64 3x3x64 convolutions with stride [1  1] and padding [1  1  1  1]
    14   'BNorm5'                 Batch Normalization   Batch normalization with 64 channels
    15   'ReLU5'                  ReLU                  ReLU
    16   'Conv6'                  Convolution           64 3x3x64 convolutions with stride [1  1] and padding [1  1  1  1]
    17   'BNorm6'                 Batch Normalization   Batch normalization with 64 channels
    18   'ReLU6'                  ReLU                  ReLU
    19   'Conv7'                  Convolution           64 3x3x64 convolutions with stride [1  1] and padding [1  1  1  1]
    20   'BNorm7'                 Batch Normalization   Batch normalization with 64 channels
    21   'ReLU7'                  ReLU                  ReLU
    22   'Conv8'                  Convolution           64 3x3x64 convolutions with stride [1  1] and padding [1  1  1  1]
    23   'BNorm8'                 Batch Normalization   Batch normalization with 64 channels
    24   'ReLU8'                  ReLU                  ReLU
    25   'Conv9'                  Convolution           64 3x3x64 convolutions with stride [1  1] and padding [1  1  1  1]
    26   'BNorm9'                 Batch Normalization   Batch normalization with 64 channels
    27   'ReLU9'                  ReLU                  ReLU
    28   'Conv10'                 Convolution           64 3x3x64 convolutions with stride [1  1] and padding [1  1  1  1]
    29   'BNorm10'                Batch Normalization   Batch normalization with 64 channels
    30   'ReLU10'                 ReLU                  ReLU
    31   'Conv11'                 Convolution           64 3x3x64 convolutions with stride [1  1] and padding [1  1  1  1]
    32   'BNorm11'                Batch Normalization   Batch normalization with 64 channels
    33   'ReLU11'                 ReLU                  ReLU
    34   'Conv12'                 Convolution           64 3x3x64 convolutions with stride [1  1] and padding [1  1  1  1]
    35   'BNorm12'                Batch Normalization   Batch normalization with 64 channels
    36   'ReLU12'                 ReLU                  ReLU
    37   'Conv13'                 Convolution           64 3x3x64 convolutions with stride [1  1] and padding [1  1  1  1]
    38   'BNorm13'                Batch Normalization   Batch normalization with 64 channels
    39   'ReLU13'                 ReLU                  ReLU
    40   'Conv14'                 Convolution           64 3x3x64 convolutions with stride [1  1] and padding [1  1  1  1]
    41   'BNorm14'                Batch Normalization   Batch normalization with 64 channels
    42   'ReLU14'                 ReLU                  ReLU
    43   'Conv15'                 Convolution           64 3x3x64 convolutions with stride [1  1] and padding [1  1  1  1]
    44   'BNorm15'                Batch Normalization   Batch normalization with 64 channels
    45   'ReLU15'                 ReLU                  ReLU
    46   'Conv16'                 Convolution           64 3x3x64 convolutions with stride [1  1] and padding [1  1  1  1]
    47   'BNorm16'                Batch Normalization   Batch normalization with 64 channels
    48   'ReLU16'                 ReLU                  ReLU
    49   'Conv17'                 Convolution           64 3x3x64 convolutions with stride [1  1] and padding [1  1  1  1]
    50   'BNorm17'                Batch Normalization   Batch normalization with 64 channels
    51   'ReLU17'                 ReLU                  ReLU
    52   'Conv18'                 Convolution           64 3x3x64 convolutions with stride [1  1] and padding [1  1  1  1]
    53   'BNorm18'                Batch Normalization   Batch normalization with 64 channels
    54   'ReLU18'                 ReLU                  ReLU
    55   'Conv19'                 Convolution           64 3x3x64 convolutions with stride [1  1] and padding [1  1  1  1]
    56   'BNorm19'                Batch Normalization   Batch normalization with 64 channels
    57   'ReLU19'                 ReLU                  ReLU
    58   'Conv20'                 Convolution           1 3x3x64 convolutions with stride [1  1] and padding [1  1  1  1]
    59   'FinalRegressionLayer'   Regression Output     mean-squared-error
