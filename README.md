# Ansible Amazon Linux Cloudwatch Logs Agent [![Build Status](https://travis-ci.org/Alexandre-io/ansible-amazon-linux-cloudwatch-logs-agent.svg?branch=master)](https://travis-ci.org/Alexandre-io/ansible-amazon-linux-cloudwatch-logs-agent)

## Doc

https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/EC2NewInstanceCWL.html

## Requirements
An Amazon Linux 2 based system

## Role Variables

`logs`, `extra_logs`: list of logs with the following keys:

| Name        | Description                | Required | Default
|-------------|----------------------------|----------|---------
| file        | Full path to log file      | Yes      |
| format      | Datetime format            | No       | None
| group_name  | CloudWatch Log Group       | Yes      |
| stream_name | CloudWatch Log Stream Name | No       | The instance id

## Playbook Example

    - hosts: servers
      vars:
        logs:
          - file: /var/log/auth.log
            format: "%b %d %H:%M:%S"
            group_name: "auth"
            stream_name: "auth-stream"
          - file: /home/ubuntu/.bash_history
            group_name: "bash_history"
      roles:
         - { role: ansible-amazon-linux-cloudwatch-logs-agent }

## License
MIT

## Author Information
Alexandre L.
