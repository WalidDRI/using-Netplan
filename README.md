# using-Netplan
configure a network interface using Netplan
To configure a network interface using Netplan, you can follow these steps:

1. Locate the Netplan configuration files: Netplan uses YAML files to configure network interfaces. The configuration files are typically stored in the `/etc/netplan/` directory. In that directory, you'll find files with a `.yaml` extension.

2. Choose the appropriate configuration file: If you have multiple network interfaces, you may have multiple configuration files in the `/etc/netplan/` directory. Select the file that corresponds to the interface you want to configure (e.g., `01-netcfg.yaml`, `50-cloud-init.yaml`, etc.). You can open the file in a text editor.

3. Edit the configuration file: Inside the configuration file, you'll find YAML syntax. The file may already contain some configuration information, so you'll need to modify or add the necessary lines. The general structure of a Netplan configuration looks like this:

```yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    eth0:
      addresses:
        - 192.168.1.100/24
      gateway4: 192.168.1.1
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
```

In the example above, `eth0` is the name of the network interface. Modify the values according to your requirements.

4. Specify the network interface settings: The configuration file should contain a section for each network interface you want to configure. For each interface, you can specify settings such as IP address, subnet mask, gateway, and DNS servers. Here are a few commonly used configuration options:

   - `addresses`: Specify the IP address and subnet mask for the interface. For example: `addresses: [192.168.1.100/24]`.
   - `gateway4`: Set the IPv4 gateway address. For example: `gateway4: 192.168.1.1`.
   - `nameservers`: Specify the DNS servers to use. For example: `nameservers: {addresses: [8.8.8.8, 8.8.4.4]}`.

   You can also configure other options like DHCP, VLANs, bridges, etc. Refer to the Netplan documentation for more advanced configurations.

5. Save the configuration file: Once you have made the necessary changes, save the file.

6. Apply the configuration changes: To apply the new configuration, run the following command:

   ```shell
   sudo netplan apply
   ```

   Netplan will read the configuration file and apply the changes to the network interface(s). If the configuration is valid, the changes will take effect immediately.

Remember to double-check your changes and ensure the YAML syntax is correct before applying the configuration. In case of any errors, Netplan will provide error messages indicating the problem in the configuration file.
