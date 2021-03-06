GRIP Intros API - Python SDK
============================

( Unofficial )


Compatibility
-------------

Requires python 3.3+

Installation
------------

    pip install grip-intros
    

Basic Usage
-----------


First of all create a client instance, supplying your api token

    from grip_intros.client import GRIPClient
    client = GRIPClient(api_key=<your api key>, test_mode=True)

    
Get a list of containers

    In [3]: containers = client.list_containers()
    In [4]: containers
    Out[4]:
        [<grip_intros.container.Container at 0x5cc7b70>, <grip_intros.container.Container at 0x4ef5330>]

        
Create a container

    In [5]: data = { "name": "My Test Container", "description": "Test" }

    In [6]: container = client.create_container(data)

    In [7]: container
    Out[7]: <grip_intros.container.Container at 0x7292370>

    In [8]: vars(container)
    Out[8]:
    {'active': 1,
     'application_id': 41,
     'branch_url': None,
     'color': None,
     'connections_count': 0,
     'date_active': None,
     'date_created': 1515512190,
     'date_updated': None,
     'description': 'Test',
    ...}
    
List Things

    In [11]: things = client.get_things(container_id=containers[1].id)

    In [12]: things
    Out[12]:
    [<grip_intros.thing.Thing at 0x6fd7cb0>,
     <grip_intros.thing.Thing at 0x6fc67f0>,
     <grip_intros.thing.Thing at 0x6fc64d0>,
     <grip_intros.thing.Thing at 0x6fc66f0>,
     <grip_intros.thing.Thing at 0x6fc6650>,
     <grip_intros.thing.Thing at 0x6fc6df0>,
     <grip_intros.thing.Thing at 0x6fc6dd0>,
     <grip_intros.thing.Thing at 0x6fc6630>,
     <grip_intros.thing.Thing at 0x6fc65f0> ...
     ]

Create a Thing

    In [13]: data = { "name": "Test", "email": "test12345@example.com" }

    In [14]: thing = client.create_thing(data)

    In [15]: thing
    Out[15]: <grip_intros.thing.Thing at 0x707fd90>

    In [16]: vars(thing)
    Out[16]: {'id': 190176, 'uri': '/1/thing/190176'}
    
Fetch a Thing

    In [17]: thing = client.get_thing(thing.id)

    In [18]: vars(thing)
    Out[18]:
    {'active': 1,
     'application_id': 41,
     'can_meet': 1,
     'can_swipe': 1,
     'categories': [],
     'categories_ids': [],
     'company_name': None,
     'current_position': {},
     'date_created': 1515512531,
     'date_updated': None,
     'email': 'test12345@example.com',
     'first_name': None,
     'gps_lat': None,
     ...
     }

More to follow....
