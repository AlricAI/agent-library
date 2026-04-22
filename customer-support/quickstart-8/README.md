# Quickstart

> **Note:** This guide will not work for Mac M1/M2 systems as they do not support Keras with TensorFlow v1.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Quickstart

**Note:** This guide will not work for Mac M1/M2 systems as they do not support Keras with TensorFlow v1. Refer to the [setup.md](setup.md) for the PyTorch guide which will work on Mac M1/M2 systems.

## Try out the step-by-step Keras classifier example

All commands are assumed to be run from the base directory at the top of this repository. We also assume other folders, like `examples`, are located under the same directory.

In this example, we will train a Keras (TensorFlow v1) CNN model, as shown below, on [MNIST](https://en.wikipedia.org/wiki/MNIST_database) data in the federated learning fashion.

```python
num_classes = 10
img_rows, img_cols = 28, 28
if K.image_data_format() == 'channels_first':
    input_shape = (1, img_rows, img_cols)
else:
    input_shape = (img_rows, img_cols, 1)

model = Sequential()
model.add(Conv2D(32, (3, 3), activation='relu', input_shape=input_shape))
model.add(Conv2D(64, (3, 3), activation='relu'))
model.add(MaxPooling2D(pool_size=(2, 2)))
model.add(Dropout(0.25))
model.add(Flatten())
model.add(Dense(128, activation='relu'))
model.add(Dropout(0.5))
model.add(Dense(num_classes, activation='softmax'))

model.compile(loss=keras.losses.categorical_crossentropy,
              optimizer=keras.optimizers.Adadelta(),
              metrics=['accuracy'])
```

### 1. Set up a running environment for IBM federated learning

We highly recommend using Conda installation for IBM federated learning. If you don't have Conda, you can install it [here](https://docs.conda.io/projects/conda/en/latest/user-guide/install).

Once Conda is installed, create a new environment for IBM federated learning by running the following. To use Keras with TensorFlow v1, you must use Python 3.7.

```sh
conda create -n <env_name> python=3.7
```

Once the conda environment is created, activate it by running the following.

```sh
conda activate <env_name>
```

Then install the IBM federated learning package using the wheel file (located in the `federated-le

*[truncated — see source for full prompt]*