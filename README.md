# Downloading and Using Llama

## Admin (Katie): Downloading 

### Create shared directory 

```
sudo mkdir shared_llms
sudo chown kkeith:users shared_llms
sudo chmod 755 shared_llms/
```

### Get Llama permissions

https://llama.meta.com/llama3


### Download llama models 

Note: you need at least Python 3.10 to run all this llama stuff; does not work on 3.12

```
conda create -y --name llama_env python==3.11
conda activate llama_env
pip install llama-stack
```

```
llama model list
llama model download --source meta --model-id  Llama3.3-70B-Instruct
llama model download --source meta --model-id  Llama3.2-3B-Instruct
llama model download --source meta --model-id  Llama3.1-405B-Instruct
```

Then move them to the `shared_llms` folder

```
sudo mv /shared/kkeith/.llama/checkpoints/Llama3.3-70B-Instruct/ ./
sudo mv /shared/kkeith/.llama/checkpoints/Llama3.2-3B-Instruct/ ./
```

### Converting to HuggingFace usable format

Downloaded `https://github.com/huggingface/transformers/blob/main/src/transformers/models/llama/convert_llama_weights_to_hf.py`

Then ran

```
conda activate llama_env
pip install torch numpy transformers
pip install 'accelerate>=0.26.0'
```

```
python convert_llama_weights_to_hf.py --input_dir Llama3.3-70B-Instruct --model_size 70B --output_dir hf-Llama3.3-70B-Instruct --llama_version 3
```

## Using Llama after downloading

Here are some examples of getting the output embeddings or using Llama for generative classification. 

Using a Jupyter Notebook, run 
```
using_llama_locally.ipynb
```