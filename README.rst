SNTP sample with Zephyr
####################################

.. contents::
   :local:
   :depth: 2

This is a SNTP sample for the nRF7002DK to get the unix time. The default SNTP sample doesn't work for the nRF7002DK as it keeps returning error ``Failed to send over UDP socket -1``

This sample is created from a combination of the `wifi station sample <https://developer.nordicsemi.com/nRF_Connect_SDK/doc/latest/nrf/samples/wifi/sta/README.html>`_, `Zephyr's SNTP sample <https://docs.zephyrproject.org/latest/samples/net/sockets/sntp_client/README.html>`_, and `these lines from the nRF91's cellular UDP sample <https://github.com/NordicDeveloperAcademy/cell-fund/blob/master/v2.4.0-v2.x.x/lesson3/cellfund_less3_exer1_solution/src/main.c#L36-L75>`_.

Requirements
################
* Built with nRF Connect SDK v2.5.0

Setup
#######
To use, we have to be put the following in ``proj.conf``:

#. SSID into ``CONFIG_STA_SAMPLE_SSID``
#. Password into ``CONFIG_STA_SAMPLE_PASSWORD``
#. Uncomment one of the security modes. E.g. ``CONFIG_STA_KEY_MGMT_WPA2``

Example output
##################
.. code-block:: console
   *** Booting nRF Connect SDK v2.5.0 ***
   [00:00:00.623,748] K
   m<inf> net_config: Initializing network
   [00:00:00.623,748] <inf> net_config: Waiting interface 1 (0x20001478) to be up...
   [00:00:00.623,901] <inf> net_config: IPv4 address: 192.168.1.99
   [00:00:00.623,962] <inf> net_config: Running dhcpv4 client...
   [00:00:00.624,267] <inf> sta: Starting nrf7002dk_nrf5340_cpuapp with CPU frequency: 64 MHz
   [00:00:01.624,328] <inf> sta: QSPI Encryption disabled
   [00:00:01.624,389] <inf> sta: Static IP address (overridable): 192.168.1.99/255.255.255.0 -> 192.168.1.1
   [00:00:03.188,385] <inf> sta: Connection requested
   [00:00:03.188,446] <inf> sta: ==================
   [00:00:03.188,476] <inf> sta: State: SCANNING
   [00:00:03.488,586] <inf> sta: ==================
   [00:00:03.488,647] <inf> sta: State: SCANNING
   [00:00:03.788,757] <inf> sta: ==================
   [00:00:03.788,787] <inf> sta: State: SCANNING
   [00:00:04.088,928] <inf> sta: ==================
   [00:00:04.088,958] <inf> sta: State: SCANNING
   [00:00:04.389,099] <inf> sta: ==================
   [00:00:04.389,129] <inf> sta: State: SCANNING
   [00:00:04.689,270] <inf> sta: ==================
   [00:00:04.689,331] <inf> sta: State: SCANNING
   [00:00:04.989,440] <inf> sta: ==================
   [00:00:04.989,471] <inf> sta: State: SCANNING
   [00:00:05.289,642] <inf> sta: ==================
   [00:00:05.289,672] <inf> sta: State: SCANNING
   [00:00:05.589,813] <inf> sta: ==================
   [00:00:05.589,843] <inf> sta: State: SCANNING
   [00:00:05.889,984] <inf> sta: ==================
   [00:00:05.890,045] <inf> sta: State: SCANNING
   [00:00:06.190,216] <inf> sta: ==================
   [00:00:06.190,216] <inf> sta: State: SCANNING
   [00:00:06.490,356] <inf> sta: ==================
   [00:00:06.490,386] <inf> sta: State: SCANNING
   [00:00:06.790,527] <inf> sta: ==================
   [00:00:06.790,557] <inf> sta: State: SCANNING
   [00:00:07.090,728] <inf> sta: ==================
   [00:00:07.090,759] <inf> sta: State: AUTHENTICATING
   [00:00:07.386,230] <inf> sta: Connected
   [00:00:07.405,181] <inf> net_dhcpv4: Received: 192.168.50.5
   [00:00:07.405,334] <inf> net_config: IPv4 address: 192.168.50.5
   [00:00:07.405,364] <inf> net_config: Lease time: 86400 seconds
   [00:00:07.405,395] <inf> net_config: Subnet: 255.255.255.0
   [00:00:07.405,426] <inf> net_config: Router: 192.168.50.1
   [00:00:07.405,548] <inf> sta: DHCP IP address: 192.168.50.5
   [00:00:07.450,714] <inf> net_config: IPv6 address: fe80::f6ce:36ff:fe00:1ece
   [00:00:08.413,635] <inf> sta: IPv4 Address found 129.250.35.251
   [00:00:08.414,001] <inf> sta: Sending SNTP IPv4 request...
   [00:00:08.627,899] <inf> sta: status: 0
   [00:00:08.627,929] <inf> sta: time since Epoch: high word: 0, low word: 1706359350
   [00:00:18.627,990] <inf> sta: Sending SNTP IPv4 request...
   [00:00:18.764,129] <inf> sta: status: 0
   [00:00:18.764,129] <inf> sta: time since Epoch: high word: 0, low word: 1706359360
   [00:00:28.764,221] <inf> sta: Sending SNTP IPv4 request...
   [00:00:28.901,824] <inf> sta: status: 0
   [00:00:28.901,824] <inf> sta: time since Epoch: high word: 0, low word: 1706359370
   [00:00:38.901,947] <inf> sta: Sending SNTP IPv4 request...
   [00:00:39.040,191] <inf> sta: status: 0
   [00:00:39.040,222] <inf> sta: time since Epoch: high word: 0, low word: 1706359380
   [00:00:49.040,283] <inf> sta: Sending SNTP IPv4 request...
   [00:00:49.177,459] <inf> sta: status: 0
   [00:00:49.177,459] <inf> sta: time since Epoch: high word: 0, low word: 1706359390

Limitations
#############
This hasn't been tested or optimised on low current consumption.