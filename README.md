# mini-sglang-GB10
deploy mini-sglang in local GB10

## Step 1: Follow mini-sglang [quick start](https://github.com/sgl-project/mini-sglang#-quick-start)'s step1 and step2

## Step 2: Download right pytorch with cuda version

If nvidia-smi gives CUDA version=13.0, run 
```
uv pip install torch==2.14.0.dev20260718 --index-url https://download.pytorch.org/whl/nightly/cu130
```

## Step 3: Verify right pytorch with cuda version

```
python -c "import torch; print(torch.cuda.is_available()); print(torch.cuda.get_device_name(0))"
```
Expected: True + NVIDIA GB10


## Step 4: Continue following remaining steps in mini-sglang [quick start](https://github.com/sgl-project/mini-sglang#-quick-start) 


## Comon Q&A
- For Error `PermissionError: [Errno 13] Permission denied: '/home/xxx/.cache/huggingface/hub/models--Qwen--Qwen3-0.6B'`, change permission of the dir: sudo chown -R xxx:xxx /home/xxx/.cache/huggingface/