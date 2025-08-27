## Intro
This is a base repository for running the [Unitree G1 Robotic's Reinforcement Learning Demo](https://support.unitree.com/home/en/G1_developer/rl_control_routine) and the [Unitree RL Gym project](https://github.com/unitreerobotics/unitree_rl_gym#).

You can also use it for any further third party development.

## Setups
### Clone the project

```bash
git clone --recurse-submodules https://github.com/Nagi-ovo/g1-rl-demo.git
```

You should also switch the `rsl_rl` library to `v1.0.2` branch:

```bash
cd third_party/rsl_rl
git checkout v1.0.2
```

### Download uv

Download `uv` by running:
```bash
wget -qO- https://astral.sh/uv/install.sh | sh
```

You can check for more information on [uv's offisional document website](https://docs.astral.sh/uv/getting-started/installation/#installation-methods).

### Download Isaac Gym

Download the folder from [https://developer.nvidia.com/isaac-gym/download](https://developer.nvidia.com/isaac-gym/download) and put it into the `third_party` folder.

### Sync the project

You can set up the entire environment by running:

```bash
uv sync
```

You can test if the Isaac Gym Library is properly installed by running:

```bash
cd third_party/isaacgym/python/examples
uv run 1080_balls_of_solitude.py
```

### Play the pre-trained policy model

Adjust the model directory in `third_party/unitree_rl_gym/deploy/deploy_mujoco/configs/g1.yaml`

```python
# policy_path: "{LEGGED_GYM_ROOT_DIR}/deploy/pre_train/g1/motion.pt"
policy_path: "{LEGGED_GYM_ROOT_DIR}/logs/g1/exported/policies/policy_lstm_1.pt"
```

Move the `policy_lstm_1.py` file to it's propossed place:

```bash
mv policy_lstm_1.py third_party/unitree_rl_gym/legged_gym/logs/g1/exported/policies/policy_lstm_1.py
```


Play the policy:

```bash
uv run  third_party/unitree_rl_gym/legged_gym/scripts/play.py --task=g1
```
