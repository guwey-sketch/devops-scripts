#!/usr/bin/env python3

import sys
import importlib.util

name = 'devops-scripts'
description = 'A collection of DevOps scripts for automation and optimization'

author = 'Your Name'
author_email = 'your_email@example.com'
copyright = '2023 Your Name'

required_packages = [
    'paramiko==2.10.0',
    'fabric==2.5.1',
    'boto3==1.22.5',
    'pytest==7.1.2'
]

external_dependencies = [
    'docker',
    'awscli'
]

def check_dependencies(packages):
    missing_packages = []
    for package_name in packages:
        try:
            spec = importlib.util.find_spec(package_name.split('==')[0])
            if spec is None:
                missing_packages.append(package_name)
        except ModuleNotFoundError:
            missing_packages.append(package_name)
        except Exception as e:
            print(f"Error checking for {package_name}: {e}")
            return False

    if missing_packages:
        print('Error: One or more required Python packages are missing:')
        for package in missing_packages:
            print(f"- {package}")
        print('Please install them using pip:')
        print(f'  pip install {" ".join(missing_packages)}')
        return False
    return True

if __name__ == '__main__':
    if not check_dependencies(required_packages):
        sys.exit(1)

    print(f'{name} - All required Python packages are installed.')