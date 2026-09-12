# LUFFY Development Repository

> 🚧 **Development Branch** - This is the main development repository for LUFFY (Learning to Reason Under Off‑Policy Guidance)

## About LUFFY

LUFFY is a reinforcement learning framework that bridges the gap between zero-RL and imitation learning by incorporating off-policy reasoning traces into the training process. This repository contains the core implementation and development work.

## 🔧 Development Status

This repository is under active development. Many features are currently being implemented or need refactoring.

## 🚀 Quick Start

⚠️ **Note**: This development version has incomplete implementations. Many features are marked as TODO and need to be completed before production use.

```bash
# Clone the repository
git clone <repository-url>
cd LUFFY

# Install dependencies
pip install -r luffy/requirements.txt

# Note: Some functionality is incomplete - check TODO list below for details
```

## 📁 Repository Structure

```
LUFFY/
├── luffy/                 # Core framework
│   ├── deepscaler/        # Scaling utilities (⚠️ API integration needed)
│   ├── verl/              # RL training components (⚠️ Some features incomplete)
│   └── ...
├── data/                  # Training data and scripts
├── eval_scripts/          # Evaluation utilities
├── exp_scripts/           # Experiment scripts
└── README.md              # This file
```

## ⚠️ Development Notes

- This is a **development version** with incomplete implementations
- Many functions contain TODO markers indicating pending work
- API integrations (OpenAI, Gemini) are currently placeholder implementations
- FSDP and distributed training features need completion


### 🔴 High Priority TODOs

- **API Integration**: OpenAI and Gemini API implementations need completion
- **Reward System**: Parallel processing and validation for reward computation  
- **FSDP Training**: Model loading and distributed training setup
- **Data Processing**: Batch dimension operations and tensor reshaping

### 📝 Complete TODO List

- [ ] **luffy/deepscaler/utils.py:45** - Add logging for API calls and errors
- [ ] **luffy/deepscaler/utils.py:46** - Support batch processing for multiple prompts
- [ ] **luffy/deepscaler/utils.py:47** - Add timeout configuration for API calls
- [ ] **luffy/deepscaler/utils.py:107** - Implement Vertex AI initialization and authentication
- [ ] **luffy/deepscaler/utils.py:108** - Configure safety settings for content generation
- [ ] **luffy/deepscaler/utils.py:109** - Set up GenerativeModel with proper system instructions
- [ ] **luffy/deepscaler/utils.py:110** - Implement retry logic with exponential backoff
- [ ] **luffy/deepscaler/utils.py:111** - Add comprehensive error handling for API access issues
- [ ] **luffy/deepscaler/utils.py:112** - Handle rate limiting and quota management
- [ ] **luffy/deepscaler/utils.py:113** - Implement response validation and text extraction
- [ ] **luffy/deepscaler/utils.py:114** - Add support for different generation configurations
- [ ] **luffy/test.py:1590** - add smaller page sizes when https://github.com/Dao-AILab/flash-attention/pull/824 is merged
- [ ] **luffy/verl/examples/split_placement/split_monkey_patch.py:141** - make a canonical logger that supports various backend
- [ ] **luffy/verl/tests/e2e/check_results.py:21** - this function needs error handling
- [ ] **luffy/verl/tests/ray/test_high_level_scheduling_api.py:25** - pass *args and **kwargs is bug prone and not very convincing
- [ ] **luffy/verl/tests/ray/test_worker_group_basics.py:43** - pass *args and **kwargs is bug prone and not very convincing
- [ ] **luffy/verl/verl/mix_src/mix_fsdp_worker.py:83** - it seems that manual offload is slowly than FSDP offload
- [ ] **luffy/verl/verl/mix_src/mix_fsdp_worker.py:207** - add transformer policy
- [ ] **luffy/verl/verl/mix_src/mix_fsdp_worker.py:226** - add more optimizer args into config
- [ ] **luffy/verl/verl/mix_src/mix_fsdp_worker.py:263** - a sharding manager that do nothing?
- [ ] **luffy/verl/verl/mix_src/mix_fsdp_worker.py:391** - here, we should return all metrics
- [ ] **luffy/verl/verl/mix_src/mix_fsdp_worker.py:517** - support DCP and save sharded checkpoints
- [ ] **luffy/verl/verl/mix_src/mix_trainer.py:90** - add other ways to estimate advantages
- [ ] **luffy/verl/verl/mix_src/mix_trainer.py:168** - support each role have individual ray_worker_group_cls,
- [ ] **luffy/verl/verl/mix_src/mix_trainer.py:293** - we have to make sure the batch size is divisible by the dp size
- [ ] **luffy/verl/verl/mix_src/mix_trainer.py:599** - make a canonical logger that supports various backend
- [ ] **luffy/verl/verl/mix_src/mix_trainer.py:637** - add response length
- [ ] **luffy/verl/verl/mix_src/mix_trainer_acc_rebatch.py:63** - we have to make sure the batch size is divisible by the dp size
- [ ] **luffy/verl/verl/mix_src/mix_trainer_acc_rebatch.py:437** - make a canonical logger that supports various backend
- [ ] **luffy/verl/verl/mix_src/mix_trainer_acc_rebatch.py:592** - check path
- [ ] **luffy/verl/verl/mix_src/mix_trainer_acc_rebatch.py:628** - from remote not implemented yet
- [ ] **luffy/verl/verl/models/llama/megatron/layers/parallel_attention.py:380** - llama does not have dropout in the config??
- [ ] **luffy/verl/verl/models/llama/megatron/layers/parallel_decoder.py:78** - add sequence parallel operator reduce_scatter here
- [ ] **luffy/verl/verl/models/llama/megatron/layers/parallel_decoder.py:86** - add sequence parallel operator all_gather here
- [ ] **luffy/verl/verl/models/llama/megatron/layers/parallel_decoder.py:90** - add sequence parallel operator reduce_scatter here
- [ ] **luffy/verl/verl/models/llama/megatron/modeling_llama_megatron.py:330** - for better performance, the sp padding should be removed at each layer. Not sure the performance gap
- [ ] **luffy/verl/verl/models/llama/megatron/modeling_llama_megatron.py:588** - for better performance, the sp padding should be removed at each layer. Not sure the performance gap
- [ ] **luffy/verl/verl/models/transformers/llama.py:88** - These transpose are quite inefficient but Flash Attention requires the layout [batch_size, sequence_length, num_heads, head_dim]. We would need to refactor the KV cache
- [ ] **luffy/verl/verl/protocol.py:114** - Optimize memory usage during tensor reshaping
- [ ] **luffy/verl/verl/protocol.py:115** - Add support for different tensor types and shapes
- [ ] **luffy/verl/verl/protocol.py:136** - Optimize tensor view operations for performance
- [ ] **luffy/verl/verl/protocol.py:137** - Add error handling for invalid batch dimensions
- [ ] **luffy/verl/verl/protocol.py:265** - we can actually lift this restriction if needed
- [ ] **luffy/verl/verl/single_controller/ray/base.py:439** - create a class with customizable name
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_3_1/llm_engine_sp.py:101** - currently is hfconfig
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_3_1/llm_engine_sp.py:145** - check get_lora_tokenizer func
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_3_1/llm_engine_sp.py:586** - check this input
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_3_1/llm_engine_sp.py:661** - we may not need to decode
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_3_1/weight_loaders.py:62** - check megatron
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_3_1/weight_loaders.py:84** - need to implement a general way to deal with prefix
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_3_1/worker.py:109** - do not use cupy
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_4_2/arg_utils.py:257** - spec config
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_4_2/config.py:136** - for multimodal model
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_4_2/hf_weight_loader.py:87** - Remove this after Mixtral is updated
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_4_2/llm_engine_sp.py:130** - currently is hfconfig
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_4_2/llm_engine_sp.py:145** - check tokenizer class
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_4_2/llm_engine_sp.py:153** - don't know what's the usage
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_4_2/llm_engine_sp.py:237** - check whether we should rebuild the CUDAGraph every iter when offload/load KVCache
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_4_2/megatron_weight_loaders.py:67** - check megatron
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_4_2/megatron_weight_loaders.py:254** - need to implement a general way to deal with prefix
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_4_2/megatron_weight_loaders.py:337** - remove dependencies from megatron
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_4_2/model_loader.py:152** - Remove this after Mixtral is updated
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_4_2/model_loader.py:191** - Remove this after Mixtral is updated
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_4_2/model_loader.py:237** - Remove this after Mixtral is updated
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_4_2/parallel_state.py:236** - this will hang
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_4_2/parallel_state.py:245** - will hang when used with device mesh
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_4_2/parallel_state.py:247** - init using device mesh
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_5_4/arg_utils.py:366** - spec config
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_5_4/config.py:191** - check whether this is necessary
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_5_4/hf_weight_loader.py:40** - Remove this after Mixtral is updated
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_5_4/llm.py:148** - check usagecontext
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_5_4/llm_engine_sp.py:271** - check whether we should rebuild the CUDAGraph every iter when offload/load KVCache
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_5_4/megatron_weight_loaders.py:67** - check megatron
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_5_4/megatron_weight_loaders.py:254** - need to implement a general way to deal with prefix
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_5_4/model_loader.py:163** - Remove this after Mixtral is updated
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_5_4/model_loader.py:203** - Remove this after Mixtral is updated
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_5_4/model_loader.py:250** - Remove this after Mixtral is updated
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_5_4/parallel_state.py:138** - check why True is not work in Ray trainer
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_5_4/parallel_state.py:165** - check why True is not work in Ray trainer
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_5_4/parallel_state.py:177** - init using device mesh (not support hybrid engine now)
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_5_4/parallel_state.py:249** - check why True is not work in Ray trainer
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_5_4/parallel_state.py:253** - init using device mesh (not support hybrid engine now)
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_5_4/worker.py:84** - we don't need driver
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_6_3/hf_weight_loader.py:37** - Remove this after Mixtral is updated
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_6_3/llm.py:147** - check usagecontext
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_6_3/llm_engine_sp.py:345** - check whether we should rebuild the CUDAGraph every iter when offload/load KVCache
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_6_3/megatron_weight_loaders.py:68** - check megatron
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_6_3/megatron_weight_loaders.py:255** - need to implement a general way to deal with prefix
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_6_3/model_loader.py:181** - Remove this after Mixtral is updated
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_6_3/model_loader.py:229** - Remove this after Mixtral is updated
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_6_3/model_loader.py:284** - Remove this after Mixtral is updated
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_6_3/parallel_state.py:144** - check why True is not work in Ray trainer
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_6_3/parallel_state.py:172** - check why True is not work in Ray trainer
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_6_3/parallel_state.py:185** - init using device mesh (not support hybrid engine now)
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_6_3/parallel_state.py:257** - check why True is not work in Ray trainer
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_6_3/parallel_state.py:262** - init using device mesh (not support hybrid engine now)
- [ ] **luffy/verl/verl/third_party/vllm/vllm_v_0_6_3/worker.py:92** - we don't need driver
- [ ] **luffy/verl/verl/trainer/fsdp_sft_trainer.py:77** - add checkpoint manager
- [ ] **luffy/verl/verl/trainer/fsdp_sft_trainer.py:159** - Implement model loading with proper initialization context
- [ ] **luffy/verl/verl/trainer/fsdp_sft_trainer.py:160** - Add support for different model types and configurations
- [ ] **luffy/verl/verl/trainer/fsdp_sft_trainer.py:161** - Implement memory-efficient model loading for large models
- [ ] **luffy/verl/verl/trainer/fsdp_sft_trainer.py:162** - Add model validation and compatibility checks
- [ ] **luffy/verl/verl/trainer/fsdp_sft_trainer.py:165** - Complete model loading implementation
- [ ] **luffy/verl/verl/trainer/fsdp_sft_trainer.py:166** - Add support for custom model architectures
- [ ] **luffy/verl/verl/trainer/fsdp_sft_trainer.py:167** - Implement proper dtype and attention configuration
- [ ] **luffy/verl/verl/trainer/fsdp_sft_trainer.py:170** - Implement gradient checkpointing configuration
- [ ] **luffy/verl/verl/trainer/fsdp_sft_trainer.py:171** - Add memory usage optimization strategies
- [ ] **luffy/verl/verl/trainer/fsdp_sft_trainer.py:172** - Configure mixed precision training settings
- [ ] **luffy/verl/verl/trainer/fsdp_sft_trainer.py:173** - Implement FSDP sharding and wrapping policies
- [ ] **luffy/verl/verl/trainer/fsdp_sft_trainer.py:174** - Add CPU offloading configuration for memory optimization
- [ ] **luffy/verl/verl/trainer/fsdp_sft_trainer.py:175** - Set up distributed training parameters properly
- [ ] **luffy/verl/verl/trainer/fsdp_sft_trainer.py:178** - Initialize FSDP wrapped model
- [ ] **luffy/verl/verl/trainer/fsdp_sft_trainer.py:301** - add a unified tracking
- [ ] **luffy/verl/verl/trainer/main_ppo.py:50** - Implement reward computation for different data sources
- [ ] **luffy/verl/verl/trainer/main_ppo.py:53** - Add support for parallel processing of reward computation
- [ ] **luffy/verl/verl/trainer/main_ppo.py:54** - Implement proper sequence decoding and validation
- [ ] **luffy/verl/verl/trainer/main_ppo.py:55** - Add thread-safe logging and debugging functionality
- [ ] **luffy/verl/verl/trainer/main_ppo.py:56** - Optimize memory usage for large batch processing
- [ ] **luffy/verl/verl/trainer/main_ppo.py:62** - Extract and validate prompt and response sequences
- [ ] **luffy/verl/verl/trainer/main_ppo.py:63** - Decode sequences to text format
- [ ] **luffy/verl/verl/trainer/main_ppo.py:64** - Apply appropriate reward function based on data source
- [ ] **luffy/verl/verl/trainer/main_ppo.py:65** - Handle edge cases and error conditions
- [ ] **luffy/verl/verl/trainer/main_ppo.py:70** - Implement batch-wise reward computation
- [ ] **luffy/verl/verl/trainer/main_ppo.py:71** - Add proper error handling and validation
- [ ] **luffy/verl/verl/trainer/ppo/ray_trainer.py:129** - add other ways to estimate advantages
- [ ] **luffy/verl/verl/trainer/ppo/ray_trainer.py:207** - add response length
- [ ] **luffy/verl/verl/trainer/ppo/ray_trainer.py:330** - support each role have individual ray_worker_group_cls,
- [ ] **luffy/verl/verl/trainer/ppo/ray_trainer.py:379** - we have to make sure the batch size is divisible by the dp size
- [ ] **luffy/verl/verl/trainer/ppo/ray_trainer.py:632** - check path
- [ ] **luffy/verl/verl/trainer/ppo/ray_trainer.py:667** - from remote not implemented yet
- [ ] **luffy/verl/verl/trainer/ppo/ray_trainer.py:880** - make a canonical logger that supports various backend
- [ ] **luffy/verl/verl/utils/checkpoint/fsdp_checkpoint_manager.py:101** - shall we remove previous ckpt every save?
- [ ] **luffy/verl/verl/utils/checkpoint/fsdp_checkpoint_manager.py:135** - address optimizer is None
- [ ] **luffy/verl/verl/utils/model.py:164** - we can make this faster
- [ ] **luffy/verl/verl/utils/model.py:272** - to find a better way to load mistral7b-rm lm_head
- [ ] **luffy/verl/verl/utils/torch_functional.py:362** - add them back
- [ ] **luffy/verl/verl/workers/actor/megatron_actor.py:225** - actually, we just need to control the sampling order.
- [ ] **luffy/verl/verl/workers/actor/megatron_actor.py:301** - we may use the new schedule instead
- [ ] **luffy/verl/verl/workers/critic/megatron_critic.py:176** - we may use the new schedule instead
- [ ] **luffy/verl/verl/workers/fsdp_workers.py:117** - it seems that manual offload is slowly than FSDP offload
- [ ] **luffy/verl/verl/workers/fsdp_workers.py:233** - add transformer policy
- [ ] **luffy/verl/verl/workers/fsdp_workers.py:252** - add more optimizer args into config
- [ ] **luffy/verl/verl/workers/fsdp_workers.py:289** - a sharding manager that do nothing?
- [ ] **luffy/verl/verl/workers/fsdp_workers.py:416** - here, we should return all metrics
- [ ] **luffy/verl/verl/workers/megatron_workers.py:57** - torch cumsum not support deterministic (used in vllm sampler),
- [ ] **luffy/verl/verl/workers/megatron_workers.py:204** - add more optimizer args into config
- [ ] **luffy/verl/verl/workers/megatron_workers.py:338** - here, we should return all metrics
- [ ] **luffy/verl/verl/workers/megatron_workers.py:478** - support vpp here
- [ ] **luffy/verl/verl/workers/megatron_workers.py:507** - add more optimizer args into config
- [ ] **luffy/verl/verl/workers/megatron_workers.py:667** - add more optimizer args into config
- [ ] **luffy/verl/verl/workers/megatron_workers.py:720** - reward model use itself tokenizer instead of sft tokenizer
- [ ] **luffy/verl/verl/workers/reward_model/megatron/reward_model.py:192** - actually, we just need to control the sampling order.
- [ ] **luffy/verl/verl/workers/reward_model/megatron/reward_model.py:233** - we may use the new schedule instead
- [ ] **luffy/verl/verl/workers/rollout/hf_rollout.py:98** - filter out the seq with no answers like ds-chat
- [ ] **luffy/verl/verl/workers/sharding_manager/fsdp_ulysses.py:49** - check how to set seed for each model
- [ ] **luffy/verl/verl/workers/sharding_manager/fsdp_ulysses.py:56** - check how to set seed for each model
- [ ] **luffy/verl/verl/workers/sharding_manager/fsdp_vllm.py:82** - offload FSDP model weights
- [ ] **luffy/verl/verl/workers/sharding_manager/fsdp_vllm.py:113** - Current impl doesn't consider FSDP with torch micro-dp
- [ ] **luffy/verl/verl/workers/sharding_manager/fsdp_vllm.py:122** - Current impl doesn't consider FSDP with torch micro-dp
- [ ] **luffy/verl/verl/workers/sharding_manager/fsdp_vllm.py:130** - shall we build a micro_dp group for vllm when integrating with vLLM?
- [ ] **luffy/verl/verl/workers/sharding_manager/megatron_vllm.py:76** - after binding to the memory buffer, we can load the checkpoint here

## 🤝 Contributing

1. Pick a TODO item from the list above
2. Implement the functionality
3. Test your implementation
4. Update this README when TODOs are completed

