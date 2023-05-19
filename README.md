# CS6910_assignment_3

1. Clone this repository
   ```bash
   git clone https://github.com/Siddharth02003/CS6910_assignment_3.git
   ```
2. Install the required packages
   ```bash
   pip3 install -r requirements.txt
   ```
Peek inside the requirements file if you have everything already installed. Most of the dependencies are common libraries.

Running the model 

```sh
python cs6910_assignment_3.py --sweep <> --inp_embed_size <> --num_enc_layers <> --num_dec_layers <> --hidden_size <> --cell_type <> --bidirectional <> --dropout <> 
```
Enter the parameter you would like to change in the place of <>. The default values of each parameter are mentioned below.
<br>

**Description of various command line arguments**<br>
1. `--sweep` : Yes or No <br>
2. `--inp_embed_size` : Size of the input embedding (Default: 256)  <br>
3. `--num_enc_layers` : Number of Encoder Layers  (Default: 2) <br>
4. `--num_dec_layers` : Number of Decoder Layers  (Default: 2) <br>
5. `--hidden_size` : Hidden layer size: Integer denoting the size of hidden layer (Default: 512) <br>
6. `--dropout` : Dropout: float value (Default:0.25)

The jupyter notebook can be directly run using colab platform in a sequential manner. 

<br/> The hyperparamter sweeps can be run using the following method
```python
do_sweep(entity_name, project_name)
```
where
  * `entity_name` : Enter the wandb entity name
  * `project_name` : Enter the wandb project name

<br/>  The various hyperparameters used are :
```python

        'inp_embed_size': {
            'values': [32,64,256]
        },
        'num_enc_layers' : {
           'values' : [1,2,3,4]
        },
        'num_dec_layers' : {
           'values' : [1,2,3,4]
        },
        'hidden_size': {
            'values': [256,512,1024]
        },
        'cell_type': {
            'values': ['RNN','LSTM','GRU'],
        },
        'bidirectional': {
            'values': [True,False]
        },
        'dropout': {
            'values': [0.25,0.3,0.4]
        }
 sweep_config = {
      'method' : 'bayes','metric' :{'name': 'validation_char_accuracy','goal': 'maximize'},
      'parameters': hyperparameters
    }
```
