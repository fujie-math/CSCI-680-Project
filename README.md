# CSCI-680 Project

This repository contains the final project for the **CSCI 680** course.

## Dependencies and Base Code

This codebase is built upon the implementation provided by **Andrew et al.** in the original **DSRL** repository:

[https://github.com/ajwagen/dsrl](https://github.com/ajwagen/dsrl)

⚠️ **Important:**
Please **first follow the instructions in the original DSRL repository** to download the required base code and correctly set up the environment **before** running the code in this project.

---

## Setup Instructions

After successfully setting up the original DSRL environment, follow the steps below.

### 1. Enter the DSRL directory

```bash
cd dsrl
```

### 2. Copy training scripts to the root directory

Copy the following files into the current directory (`./`):

* `train_dsrl_r.py`
* `train_dsrl_res.py`
* `train_dsrl_res_na.py`

### 3. Copy configuration file

Copy the configuration file:

* `dsrl_can_new.yaml`

into:

```text
./cfg/robomimic/
```

### 4. Replace the `__init__.py` file

Replace the following file:

```text
./stable-baselines3/stable_baselines3/__init__.py
```

with the provided `__init__.py` file from this project.

### 5. Add custom DSRL modules

Copy the following folders:

* `dsrl_r`
* `dsrl_res`
* `dsrl_res_na`

into:

```text
./stable-baselines3/stable_baselines3/
```

---

## Training the Model

After completing the setup steps above, you can start training the model by running:

```bash
python train_dsrl_res_na.py \
  --config-path=cfg/robomimic \
  --config-name=dsrl_can_new.yaml \
  env.n_envs=32 \
  train.action_magnitude=0.3 \
  train.noise_magnitude=0.1 \
  train.res_scale=0.5 \
  train.noise_scale=0.5
```

This command starts training our **newly proposed hybrid policy**.

---

## Parameter Explanation

* `train.action_magnitude`
  Controls the action magnitude of the **residual policy**.

* `train.noise_magnitude`
  Controls the noise level of the **noise policy**.

* `train.res_scale`
  Scaling factor for the **residual policy** in the hybrid policy.

* `train.noise_scale`
  Scaling factor for the **noise policy** in the hybrid policy.

---

## Notes

* Ensure the original DSRL repository is correctly installed and functional before applying these modifications.
* All paths are relative to the `dsrl` directory unless otherwise specified.

