
# deepspeed-belle-test

=======
# 開docker:
	docker run -it --runtime=nvidia --shm-size="100g"   -v your_path/BELLE/train/dschat_train_v1:/workspace/BELLE-train   -v your_model_path:/root/.cache/huggingface/hub   belleagi/belle:v1.0 /bin/bash

# 用的模型:
	model_name = "meta-llama/Meta-Llama-3-8B"
	model_name = "meta-llama/Llama-2-13b-chat-hf"
	model_name = "internlm/internlm2-wqx-20b"
	model_name = "google/gemma-2-27b"
	model_name = "01-ai/Yi-1.5-34B-Chat"

# 登入token:
	HF_AUTH_TOKEN=your_token

# 執行程式碼:
	單卡:bash training_scripts/single_gpu/run_LoRA.sh output-lora 3
	多卡:bash training_scripts/single_node/run_LoRA.sh output-lora 3

# 可能遇到錯誤:
	1.
		KeyError: 'lm_head.weight'
		解決:pip install --upgrade transformers
	2.
		NotImplementedError: Loading a dataset cached in a LocalFileSystem is not supported.
		解決:pip install --upgrade datasets
	3.
		解決:pip install --upgrade deepspeed
