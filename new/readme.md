
## Step 1: 
- Make sure you are in the directory of the `distributed-llama`
Step 2: 
- On workers node run this command (make sure you are in the directory of the `distributed-llama`). 
```bash
./dllama worker --port 9999 --nthreads 1 --gpu-index 0
```
```bash
./dllama worker --port 10000 --nthreads 1 --gpu-index 0
```
## Step 3: 
- On root node (For now lets assume PC1) you need to run this command. 
- In PC1 `--gpu-index 1` on other nodes it will be `0`. 
### For llama3.2 3b Instruct Q4 model Process 1:
```bash
 ./dllama chat   --port 9999   --model models/llama3_2_3b_instruct_q40/dllama_model_llama3_2_3b_instruct_q40.m   --tokenizer models/llama3_2_3b_instruct_q40/dllama_tokenizer_llama3_2_3b_instruct_q40.t   --buffer-float-type q80   --nthreads 1   --max-seq-len 8192   --workers 192.168.1.5:9999 192.168.1.2:9999 192.168.1.4:9999 --gpu-index 1
```

### For llama3.2 3b Instruct Q4 model Process 2:
```bash
 ./dllama chat   --port 10000   --model models/llama3_2_3b_instruct_q40/dllama_model_llama3_2_3b_instruct_q40.m   --tokenizer models/llama3_2_3b_instruct_q40/dllama_tokenizer_llama3_2_3b_instruct_q40.t   --buffer-float-type q80   --nthreads 1   --max-seq-len 8192   --workers 192.168.1.5:10000 192.168.1.2:10000 192.168.1.4:10000 --gpu-index 1
```

### For llama3.3 70b Instruct Q4 model:
```bash
./dllama chat   --port 9999   --model models/llama3_3_70b_instruct_q40/dllama_model_llama3_3_70b_instruct_q40.m   --tokenizer models/llama3_3_70b_instruct_q40/dllama_tokenizer_llama3_3_70b_instruct_q40.t   --buffer-float-type q80   --nthreads 1   --max-seq-len 8192   --workers 192.168.1.5:9999 192.168.1.2:9999 192.168.1.4:9999 --gpu-index 1
```
### For ChatBot Application Run this command : 
**For llama3.2 3b Instruct Q4 model Process 1:**
```bash
./dllama-api \
  --port 9999 \
  --model models/llama3_2_3b_instruct_q40/dllama_model_llama3_2_3b_instruct_q40.m \
  --tokenizer models/llama3_2_3b_instruct_q40/dllama_tokenizer_llama3_2_3b_instruct_q40.t \
  --buffer-float-type q80 \
  --nthreads 1 \
  --max-seq-len 8192 \
  --workers 192.168.1.5:9999 192.168.1.2:9999 192.168.1.4:9999 \
  --gpu-index 1
```

**For llama3.2 3b Instruct Q4 model Process 2:**
```bash
./dllama-api \
  --port 9999 \
  --model models/llama3_2_3b_instruct_q40/dllama_model_llama3_2_3b_instruct_q40.m \
  --tokenizer models/llama3_2_3b_instruct_q40/dllama_tokenizer_llama3_2_3b_instruct_q40.t \
  --buffer-float-type q80 \
  --nthreads 1 \
  --max-seq-len 8192 \
  --workers 192.168.1.5:9999 192.168.1.2:9999 192.168.1.4:9999 \
  --gpu-index 1
```


**For For llama3.3 70b Instruct Q4 model**
```bash
./dllama-api \
  --port 9999 \
  --model models/llama3_3_70b_instruct_q40/dllama_model_llama3_3_70b_instruct_q40.m \
  --tokenizer models/llama3_3_70b_instruct_q40/dllama_tokenizer_llama3_3_70b_instruct_q40.t \
  --buffer-float-type q80 \
  --nthreads 1 \
  --max-seq-len 8192 \
  --workers 192.168.1.5:9999 192.168.1.2:9999 192.168.1.4:9999 \
  --gpu-index 1
```

```bash
./dllama-api \
  --port 10001 \
  --model models/llama3_3_70b_instruct_q40/dllama_model_llama3_3_70b_instruct_q40.m \
  --tokenizer models/llama3_3_70b_instruct_q40/dllama_tokenizer_llama3_3_70b_instruct_q40.t \
  --buffer-float-type q80 \
  --nthreads 1 \
  --max-seq-len 8192 \
  --workers 192.168.1.5:9999 192.168.1.2:9999 192.168.1.4:9999 \
  --gpu-index 1
```



## Step 4:
### Run this command on the root/server/pc1 node: 
Make sure you are in the directory where you have the  `chatbot.html` file. 
`python3 -m http.server 8080`
Copy and Paste this command on the Browser (you can run this command to any server/worker/root to accesss the chatbot).
`http://192.168.1.1:8080/chatbot.html`


