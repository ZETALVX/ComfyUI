# ACE-Step 1.5 LoRA Training Configs

This file contains a few practical LoRA training configurations for ACE-Step 1.5 in ComfyUI.

These are not universal “best settings”.  
They are starting points for experimenting with different GPUs, dataset sizes, and style goals.

---

## Basic idea

Lower settings are safer and use less VRAM.  
Higher settings can learn a stronger style, but may increase VRAM usage and overfitting risk.

The most important values are:

- `lora_rank` → LoRA capacity
- `lora_alpha` → LoRA strength scaling
- `learning_rate` → how fast the LoRA learns
- `max_epochs` → how long it trains
- `gradient_accumulation` → helps stabilize training
- `target_modules` → transformer layers trained by the LoRA

Dataset quality usually matters more than pushing the settings higher.

```text
## Very Safe / Low VRAM
# Use this if you get OOM errors or just want a quick test.

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

# Good for quick experiments on small datasets.

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

# This is close to one of the configs I used in my tests.

## Balanced / Recommended

# Good starting point for a clean dataset of around 15–30 tracks.

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

# Use this if you want the LoRA to have a stronger influence.

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

# Use only if you have enough VRAM and a very consistent dataset.

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

# For acoustic, medieval, folk, lute, flute, tavern, or choir-like datasets.

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

# For techno-pop, brass, summer festival, EDM, viral loop-style datasets.

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

# Try this order:

lower lora_rank
keep batch_size at 1
reduce audio duration / use shorter clips
lower gradient_accumulation
restart ComfyUI before training
avoid keeping unnecessary models loaded
Practical advice
Start small.
Save often.
Compare different epochs.
The final checkpoint is not always the best one.
A smaller clean dataset can beat a larger messy one.
Keep one clear musical identity per LoRA.
Use a custom activation tag and keep it consistent.
