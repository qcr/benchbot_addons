**NOTE: this software is part of the BenchBot software stack, and not intended to be run in isolation (although it can be installed independently through pip & if desired). For a working BenchBot system, please install the BenchBot software stack by following the instructions [here](https://github.com/roboticvisionorg/benchbot).**

# BenchBot Add-ons Manager

![Sample of all the different add-ons available](./docs/benchbot_addons.gif)

The BenchBot Add-ons Manager allows you to use BenchBot with a wide array of additional content, and customise your installation to suite your needs. Semantic Scene Understanding not your thing? Install the Semantic Question Answering add-ons instead. Want to create your own content? Write some basic YAML files to make your own add-ons. Need to re-use existing content? Simply include a dependency on that add-on. Add-ons are all about making BenchBot whatever you need it to be&mdash;build a BenchBot for your research problems, exactly as you need it.

Add-ons

## Installing and Using the add-ons manager

In general, you won't use the add-ons manager directly. Instead you interact with the [BenchBot software stack](https://github.com/roboticvisionorg/benchbot), which uses the add-ons manager to manage and access add-ons.

The manager is a Python package if you do find you want to use it directly, and installable with pip. Run the following in the root directory where the repository was cloned:

```
u@pc:~$ pip install .
```

The manager can then be imported and used to manage installation, loading, accessing, processing, and updating add-ons. Some of types of functionality are shown below:

```python
from benchbot_addons import manager as bam

# Check if example with 'name' = 'hello_scd' exists
bam.exists('examples', [('name', 'hello_scd')])

# Find all installed environments
bam.find_all('environments')

# Get a list of the names for all installed tasks
bam.get_field('tasks', 'name')

# Get a list of (name, variant) pairs for all installed environments
bam.get_fields('environments', ['name', 'variant'])

# Find a robot with 'name' = 'carter'
bam.get_match('robots', [('name', 'carter')])

# Get the 'results_format' value for the task called 'scd:passive:ground_truth'
bam.get_value_by_name('tasks', 'scd:passive:ground_truth', 'results_format')

# Load YAML data for all installed ground truths
bam.load_yaml_list(bam.find_all('ground_truths', extension='json'))

# Install a list of comma-separated add-ons
bam.install_addons('ssu,sqa')

# Install a specific add-on (& it's dependencies)
bam.install_addon('tasks_ssu')

# Print the list of currently installed add-ons, & officially available add-ons
bam.print_state()

# Uninstall all add-ons
bam.remove_addons()

# Uninstall a string separated list of add-ons
bam.remove_addon('ssu,sqa')
```

## How to add your own add-ons

## Add-ons format specification
