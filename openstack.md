

<h4> Openstack </h4>
<ul> 
  <li> <a href="https://developer.openstack.org/firstapp-shade/getting_started.html"> Openstack python SDK guide </a> </li>
  <li> <a href="https://developer.openstack.org/firstapp-libcloud/getting_started.html"> SDKs - multiple verions of SDK </a> </li>
  <li> <a href="https://docs.openstack.org/openstacksdk/latest/user/connection.html"> Openstack Connection api </a> </li>
  <li> <a href="https://docs.openstack.org/openstacksdk/latest/user/proxies/"> Openstack proxies api </a> </li>
  
</ul>


<h4> OpenStack api usage </h4>
'''

    def create_image_snapshot(self, stack, name_or_id, snapshot_name):
        try:
            _conn = self.get_connection(stack)
            return _conn.create_image_snapshot(snapshot_name, name_or_id, wait=True)
        except Exception as exc:
            handle_and_raise(exc)

    def create_volume_from_snapshot(self, stack, vol_snapshot):
        try:
            _conn = self.get_connection(stack)
            return _conn.create_volume(size=vol_snapshot['volume_size'],
                                       snapshot_id=vol_snapshot['snapshot_id'], wait=True)
        except Exception as exc:
            handle_and_raise(exc)

    def delete_instance_interface(self, stack, name_or_id):
        try:
            _conn = self.get_connection(stack)
            interfaces = _conn.compute.server_interfaces(name_or_id)
            if interfaces:
                il = list(interfaces)
                for interface in il:
                    _conn.compute.delete_server_interface(interface, name_or_id)
        except Exception as exc:
            handle_and_raise(exc)

'''

