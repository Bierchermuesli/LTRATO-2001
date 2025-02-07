Step 4: pyATS Shell Useful Libraries
####################################

**Value Proposition:** Explore additional pyATS libraries and learn how to use them in the pyATS shell.

Another useful library is the **Dq**. The **Dq** library is used to query the data structure more conveniently.

To use the **Dq** library, you need to follow the steps below:

#. Create variables (Python objects) to call devices easily (csr - 'csr1000v-1' device).

    .. code-block:: python

        csr = testbed.devices["csr1000v-1"]

#. Connect and collect the output from the CSR device.

    .. code-block:: python

        csr.connect()
        csr_output = csr.parse("show ip route")

#. Explore csr_output and try to find the routes for **OSPF**.

    .. code-block:: python

        {'vrf': {'default': {'address_family': {'ipv4': {'routes': {'10.0.0.4/30': {'route': '10.0.0.4/30',
        'active': True,
        'metric': 41,
        'route_preference': 110,
        'source_protocol_codes': 'O',
        'source_protocol': 'ospf',
        'next_hop': {'next_hop_list': {1: {'index': 1,
            'next_hop': '10.0.0.18',
            'updated': '18:21:31',
            'outgoing_interface': 'GigabitEthernet3'},
            2: {'index': 2,
            'next_hop': '10.0.0.14',
            'updated': '18:21:31',
            'outgoing_interface': 'GigabitEthernet2'}}}},
        '10.0.0.8/30': {'route': '10.0.0.8/30',
        'active': True,
        'metric': 51,
        'route_preference': 110,
        'source_protocol_codes': 'O',
        'source_protocol': 'ospf',
        'next_hop': {'next_hop_list': {1: {'index': 1,
            'next_hop': '10.0.0.18',
            'updated': '18:21:26',
            'outgoing_interface': 'GigabitEthernet3'},
            2: {'index': 2,
            'next_hop': '10.0.0.14',
            'updated': '18:21:26',
            'outgoing_interface': 'GigabitEthernet2'}}}},
        '10.0.0.12/30': {'route': '10.0.0.12/30',
        'active': True,
        'source_protocol_codes': 'C',
        'source_protocol': 'connected',
        'next_hop': {'outgoing_interface': {'GigabitEthernet2': {'outgoing_interface': 'GigabitEthernet2'}}}},
        '10.0.0.13/32': {'route': '10.0.0.13/32',
        'active': True,
        'source_protocol_codes': 'L',
        'source_protocol': 'local',
        'next_hop': {'outgoing_interface': {'GigabitEthernet2': {'outgoing_interface': 'GigabitEthernet2'}}}},
        '10.0.0.16/30': {'route': '10.0.0.16/30',
        'active': True,
        'source_protocol_codes': 'C',
        'source_protocol': 'connected',
        'next_hop': {'outgoing_interface': {'GigabitEthernet3': {'outgoing_interface': 'GigabitEthernet3'}}}},
        '10.0.0.17/32': {'route': '10.0.0.17/32',
        'active': True,
        'source_protocol_codes': 'L',
        'source_protocol': 'local',
        'next_hop': {'outgoing_interface': {'GigabitEthernet3': {'outgoing_interface': 'GigabitEthernet3'}}}},
        '192.168.0.1/32': {'route': '192.168.0.1/32',
        'active': True,
        'metric': 2,
        'route_preference': 110,
        'source_protocol_codes': 'O',
        'source_protocol': 'ospf',
        'next_hop': {'next_hop_list': {1: {'index': 1,
            'next_hop': '10.0.0.18',
            'updated': '18:21:32',
            'outgoing_interface': 'GigabitEthernet3'},
            2: {'index': 2,
            'next_hop': '10.0.0.14',
            'updated': '18:21:32',
            'outgoing_interface': 'GigabitEthernet2'}}}},
        '192.168.0.3/32': {'route': '192.168.0.3/32',
        'active': True,
        'source_protocol_codes': 'C',
        'source_protocol': 'connected',
        'next_hop': {'outgoing_interface': {'Loopback0': {'outgoing_interface': 'Loopback0'}}}},
        '192.168.100.1/32': {'route': '192.168.100.1/32',
        'active': True,
        'metric': 52,
        'route_preference': 110,
        'source_protocol_codes': 'O',
        'source_protocol': 'ospf',
        'next_hop': {'next_hop_list': {1: {'index': 1,
            'next_hop': '10.0.0.18',
            'updated': '18:21:26',
            'outgoing_interface': 'GigabitEthernet3'},
            2: {'index': 2,
            'next_hop': '10.0.0.14',
            'updated': '18:21:26',
            'outgoing_interface': 'GigabitEthernet2'}}}}}}}}}}

.. note::
    
    It's much simpler to use the **Dq** library to query the output of the device.

#. Import the **Dq** library.

    .. code-block:: python

        from genie.utils import Dq

#. Make a specific query to the output of the CSR device.

    .. code-block:: python

        csr_output.q.contains('ospf').get_values('routes')

.. tip::
    
    The **Dq** library is very useful to query the output of the device. You can find more information about the **Dq** library in the `pyATS Useful Libraries <https://pubhub.devnetcloud.com/media/genie-docs/docs/userguide/utils/index.html>`_.


.. sectionauthor:: Luis Rueda <lurueda@cisco.com>, Jairo Leon <jaileon@cisco.com>

