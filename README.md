# Ansible Collection - cobbler.cobbler

This collection contains an inventory plugin for collecting iventory
information from a cobbler server.

## Installation

You can install the collection from [Ansible Galaxy](https://galaxy.ansible.com/cobbler/cobbler)
by running `ansible-galaxy collection install cobbler.cobbler` (Ansible 2.9 and later).

## Configuration

You can define one or more inventory files with suffix `.cobbler.{yaml,yml}` as follows:

```
plugin: cobbler
url: https://cobbler.example.com/cobbler_api
```

## Documentation
```
> INVENTORY    (plugins/inventory/cobbler.py)

        Get inventory hosts from the cobbler service. Uses a configuration file as an inventory source, it must end in ``.cobbler.yml``
        or ``.cobbler.yaml`` and has a ``plugin: cobbler`` entry.

OPTIONS (= is mandatory):

- cache
        Toggle to enable/disable the caching of the inventory's source data, requires a cache plugin setup to work.
        [Default: False]
        set_via:
          env:
          - name: ANSIBLE_INVENTORY_CACHE
          ini:
          - key: cache
            section: inventory
        
        type: bool

- cache_connection
        Cache connection data or path, read cache plugin documentation for specifics.
        [Default: (null)]
        set_via:
          env:
          - name: ANSIBLE_CACHE_PLUGIN_CONNECTION
          - name: ANSIBLE_INVENTORY_CACHE_CONNECTION
          ini:
          - key: fact_caching_connection
            section: defaults
          - key: cache_connection
            section: inventory
        
        type: str

- cache_plugin
        Cache plugin to use for the inventory's source data.
        [Default: memory]
        set_via:
          env:
          - name: ANSIBLE_CACHE_PLUGIN
          - name: ANSIBLE_INVENTORY_CACHE_PLUGIN
          ini:
          - key: fact_caching
            section: defaults
          - key: cache_plugin
            section: inventory
        
        type: str

- cache_prefix
        Prefix to use for cache plugin files/tables
        [Default: ansible_inventory_]
        set_via:
          env:
          - name: ANSIBLE_CACHE_PLUGIN_PREFIX
          - name: ANSIBLE_INVENTORY_CACHE_PLUGIN_PREFIX
          ini:
          - key: fact_caching_prefix
            section: default
          - key: cache_prefix
            section: inventory
        

- cache_timeout
        Cache duration in seconds
        [Default: 3600]
        set_via:
          env:
          - name: ANSIBLE_CACHE_PLUGIN_TIMEOUT
          - name: ANSIBLE_INVENTORY_CACHE_TIMEOUT
          ini:
          - key: fact_caching_timeout
            section: defaults
          - key: cache_timeout
            section: inventory
        
        type: int

- exclude_profiles
        profiles to exclude from inventory
        [Default: []]
        type: list

- group
        group to place all hosts into
        [Default: cobbler]

- group_by
        keys to group hosts by
        [Default: [u'mgmt_classes', u'owners', u'status']]
        type: list

- group_prefix
        prefix to apply to cobbler groups
        [Default: cobbler_]

- password
        cobbler authentication password
        [Default: (null)]
        set_via:
          env:
          - name: COBBLER_PASSWORD
        

= plugin
        the name of this plugin, it should always be set to 'cobbler' for this plugin to recognize it as it's own.
        (Choices: cobbler)

- url
        url to cobbler
        [Default: http://cobbler/cobbler_api]
        set_via:
          env:
          - name: COBBLER_SERVER
        

- user
        cobbler authentication user
        [Default: (null)]
        set_via:
          env:
          - name: COBBLER_USER
        

- want_facts
        Toggle, if True the plugin will retrieve host facts from the server
        [Default: True]
        type: boolean


NAME: cobbler

PLUGIN_TYPE: inventory

EXAMPLES:

# my.cobbler.yml
plugin: cobbler
url: http://cobbler/cobbler_api
user: ansible-tester
password: secure
```
