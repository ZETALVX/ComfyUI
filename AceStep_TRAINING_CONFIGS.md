# ACE-Step 1.5 LoRA Training Configs

This file contains a few practical LoRA training configurations for ACE-Step 1.5 in ComfyUI.

These are not universal “best settings”.  
They are starting points for experimenting with different GPUs, dataset sizes, and style goals.

---

## Basic idea

Lower settings are safer and use less VRAM.  
Higher settings can learn a stronger style, but may increase VRAM usage and overfitting risk.

### Key parameters

- `lora_rank` → LoRA capacity  
- `lora_alpha` → LoRA strength scaling  
- `learning_rate` → how fast the LoRA learns  
- `max_epochs` → training duration  
- `gradient_accumulation` → stabilizes training  
- `target_modules` → transformer layers used  

👉 Dataset quality matters more than pushing values higher.

---

## Very Safe / Low VRAM

Use this if you get OOM errors or want a quick test.

lora_rank: 8
lora_alpha: 8
lora_dropout: 0.05
learning_rate: 0.00005
max_epochs: 40
batch_size: 1
gradient_accumulation: 1
save_every_n_epochs: 10
seed: 42
warmup_steps: 50
weight_decay: 0.01
max_grad_norm: 0.5
target_modules: q_proj,k_proj,v_proj,o_proj

Light Test

Good for quick experiments on small datasets.

lora_rank: 12
lora_alpha: 12
lora_dropout: 0.05
learning_rate: 0.00006
max_epochs: 60
batch_size: 1
gradient_accumulation: 2
save_every_n_epochs: 10
seed: 42
warmup_steps: 120
weight_decay: 0.015
max_grad_norm: 0.5
target_modules: q_proj,k_proj,v_proj,o_proj

👉 Close to one of the configs used in testing.

Balanced / Recommended

Good starting point for ~15–30 tracks dataset.

lora_rank: 16
lora_alpha: 16
lora_dropout: 0.05
learning_rate: 0.00008
max_epochs: 80
batch_size: 1
gradient_accumulation: 2
save_every_n_epochs: 10
seed: 42
warmup_steps: 100
weight_decay: 0.01
max_grad_norm: 1.0
target_modules: q_proj,k_proj,v_proj,o_proj
Stronger Style Learning

Use this if you want a stronger LoRA effect.

lora_rank: 24
lora_alpha: 24
lora_dropout: 0.05
learning_rate: 0.00008
max_epochs: 100
batch_size: 1
gradient_accumulation: 2
save_every_n_epochs: 20
seed: 42
warmup_steps: 120
weight_decay: 0.01
max_grad_norm: 1.0
target_modules: q_proj,k_proj,v_proj,o_proj
High Capacity / Experimental

Use only with enough VRAM and a clean dataset.

lora_rank: 32
lora_alpha: 32
lora_dropout: 0.05
learning_rate: 0.00008
max_epochs: 120
batch_size: 1
gradient_accumulation: 4
save_every_n_epochs: 20
seed: 42
warmup_steps: 150
weight_decay: 0.01
max_grad_norm: 1.0
target_modules: q_proj,k_proj,v_proj,o_proj
Medieval / Acoustic Style Example

For lute, flute, choir, tavern, folk-style datasets.

lora_rank: 16
lora_alpha: 16
lora_dropout: 0.05
learning_rate: 0.00006
max_epochs: 80
batch_size: 1
gradient_accumulation: 2
save_every_n_epochs: 10
seed: 42
warmup_steps: 100
weight_decay: 0.015
max_grad_norm: 0.5
target_modules: q_proj,k_proj,v_proj,o_proj
Festival / Electronic Style Example

For EDM, techno-pop, brass, viral loop tracks.

lora_rank: 16
lora_alpha: 16
lora_dropout: 0.05
learning_rate: 0.00008
max_epochs: 80
batch_size: 1
gradient_accumulation: 2
save_every_n_epochs: 10
seed: 42
warmup_steps: 100
weight_decay: 0.01
max_grad_norm: 1.0
target_modules: q_proj,k_proj,v_proj,o_proj
If you get OOM

Try this order:

Lower lora_rank
Keep batch_size = 1
Use shorter audio clips
Lower gradient_accumulation
Restart ComfyUI
Close other models / workflows
Practical advice
Start small
Save often
Compare different epochs
Final checkpoint is not always the best
Clean dataset > large dataset
Keep one clear style per LoRA
Use a consistent activation tag

