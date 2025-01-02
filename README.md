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
```

## Using Llama after downloading