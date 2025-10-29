#!/usr/bin/env python3

name = 'devops-scripts'
description = 'A collection of DevOps scripts for automation and optimization'

author = 'Your Name'
author_email = 'your_email@example.com'
copyright = '2023 Your Name'

requirements = [
    'paramiko==2.10.0',
    'fabric==2.5.1',
    'boto3==1.22.5',
    'pytest==7.1.2'
]

dependencies = [
    'docker',
    'awscli'
]

# Check if requirements are met
try:
    import paramiko
    import fabric
    import boto3
    import pytest
except ImportError:
    print(f'Error: One or more required dependencies are missing.')
    print('Please install them using pip: `pip install -r requirements.txt`')
    exit(1)