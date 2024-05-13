# Novelty Search with Local Competition (NSLC)


A more detailed README will be added soon.

The algorithm is base on [NSLC paper](https://dl.acm.org/doi/10.1145/2001576.2001606) by Joel Lehman and Kenneth O. Stanley. or [here](https://www.researchgate.net/publication/220743050_Evolving_a_diversity_of_creatures_through_novelty_search_and_local_competition). or The full thesis of Joel Lehman can be found [here](http://joellehman.com/lehman-dissertation.pdf)

To test the program, execute either `python test_RL.py MAP-ELITE` from within the test folder. Additional options are available in the test_RL.py files, as well as within the configuration files located in the config folder.

To facilitate comparisons, an ANN runner built with PyTorch is also available. To use it, uncomment the line start_config_path = "./config/config_ann/RL/" in test_RL.py, and comment out the corresponding SNN configuration line start_config_path = "./config/config_snn/RL/"

A more complete version with more algorithms and more examples is also available at: https://github.com/OlivierBelan/Evo-Sim (mainly NeuroEvolution algorithms)


During the installation of pybullet, if you encounter the following error:
```AttributeError: 'dict' object has no attribute 'env_specs'```
You can fix it by changing the file ```pybullet_envs/__init__.py``` the section:
```python
def register(id, *args, **kvargs):
  if id in registry.env_specs:
    return
  else:
    return gym.envs.registration.register(id, *args, **kvargs)
```
to:
```python
def register(id, *args, **kvargs):
  if id in registry:
    return
  else:
    return gym.register(id, *args, **kvargs)
```