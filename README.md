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

Expected:


<img width="624" height="539" alt="image" src="https://github.com/user-attachments/assets/73249e68-c690-4b73-9de1-559c1eb1c415" />


## Comon Q&A
- For Error `PermissionError: [Errno 13] Permission denied: '/home/xxx/.cache/huggingface/hub/models--Qwen--Qwen3-0.6B'`, change permission of the dir: sudo chown -R xxx:xxx /home/xxx/.cache/huggingface/

- For Error `torch.distributed.DistNetworkError: The server socket has failed to listen on any local network address. port: 1920, useIpv6: false, code: -98, name: EADDRINUSE, message: address already in use`, change port ```python -m minisgl --model "Qwen/Qwen3-0.6B" --shell --port 1921```


- For Error RuntimeError: ... TllmGenFmhaRunner ... Unsupported architecture, the auto-selected trtllm attention backend does not support GB10 (sm_121). Use --attention-backend fi (flashinfer) instead:

```python -m minisgl --model "Qwen/Qwen3-0.6B" --shell --attention-backend fi```
