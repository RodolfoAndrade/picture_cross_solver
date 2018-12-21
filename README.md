# picture_cross_solver



Picture Cross or Nonogram is a puzzle in which a matrix must be filled to form an image. to fill the matrix you have to respect the number of pixels displayed in the upper side for the columns and the left side for the lines.

for more information please read this Wikipedia articles: https://en.wikipedia.org/wiki/Nonogram.



This project used a simple multilayer neural network to solve a picture cross problem.



## Getting Started



to run these notebooks on your computer you have to install anaconda or miniconda with python 3.7. after installation please follow the tutorials to create an environment and install the prerequisites.



## Prerequisites

numpy        1.15.4


pandas        0.23.4


Keras        2.2.4


matplotlib    3.0.1



## more information



this project used a 4x4 matrix. this matrix allows to 2^(4x4)=2^(16)=65536 combinations or image. you can see how the dataset was generated on the notebook create_dataset.ipynb. 
the tips to solve the image is on saved on data_x_4x4.npy inside the dataset folder. and the image is on data_y_4x4.npy.

before sending the data to the mlp the dataset is shuffle and the data_x is divided by the maximum possibility which in this case of 4x4 matrix is 4. the data_y is transformed so that the zeros turn into -1 and the ones remain ones.

after the training, the mlp was able to solve 50945 (77.74%) of the total cases. the other 14591 cases were not possible to solve because of ambiguity.

there were cases in which same x's resulted in different y's. ideally, it would be the cases where each different x resulted in each different y, such as 1 to 1 proportion.

therefore it would be impossible to solve 100% of the cases. but how much cases it was expected to solve? np.unique(data_x) would result in the unique x array, but it would contain the one x that resulted in different y. because of that, to know the precise number of cases which the mlp would solve we need to exclude all of these x's.

in the create_dataset notebook, we count for all unique array how many appeared in the data_x. if it appeared more than 2, then it means it could not be solved. in the end, we counted these cases and it summed to 13174 cases.

This number of cases which could not be solved was close enough for our cases that got it wrong. It could be possible that adding more neurons to the neural network the number could be reached. but I do not have a powerful computer here and it was tanking more than half a day, so I will leave it like this.