# Ansible Role: Logstash Forwarder

[![Build Status](https://travis-ci.org/bwits/ansible-logstash-forwarder.svg?branch=master)](https://travis-ci.org/bwits/ansible-logstash-forwarder)

An Ansible Role that installs Logstash Forwarder on RedHat/CentOS

## Reference

geerlingguy/ansible-role-logstash-forwarder

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    logstash_forwarder_logstash_server: localhost
    logstash_forwarder_logstash_server_port: 5000

The central Logstash server/port to which logstash-forwarder should connect.

    logstash_ssl_dir: /etc/pki/logstash
    logstash_forwarder_ssl_certificate_file: logstash-forwarder-example.crt

The location and filename of the SSL certificate logstash-forwarder will use to authenticate to the logstash server. For the `logstash_forwarder_ssl_certificate_file`, you can provide a path relative to the role directory, or an absolute path to the file.

    logstash_forwarder_files:
      - paths:
          - /var/log/messages
          - /var/log/auth.log
        fields:
          type: syslog
      - paths:
          - /var/log/boot.log
        fields:
          type: syslog

Configuration of files monitored by logstash-forwarder. You can add more sets of files by adding to the list with another set of files; see `defaults/main.yml` for an example.

## Dependencies

None.

## Example Playbook

    - hosts: all
      roles:
        - { role: bwits.logstash-forwarder tags: logstash-forwarder }

## License

MIT / BSD

## Author Information

This role was originally created by [Jeff Geerling](https://github.com/geerlingguy), I updated to focus for centos system with ansible v2+ features and multiple application logs supported. 
