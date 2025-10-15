# CCNA-switch-virtual-interface

-pick a good ip range for the pcs make sure no overlap-

pc0 vlan 10 --> ip address=192.168.0.2, subnet mask=255.255.255.252, default gateway=192.168.0.1

pc1 vlan 20 --> ip address=192.168.0.6, subnet mask=255.255.255.252, default gateway=192.168.0.5

--------------------------------------------------------------------------------------------------

switch access layer

\>en

#conf t

fig#int ra f0/1-2

range-if#sw mo acc

range-if#exit

fig#vlan 10

vlan#exit

fig#vlan 20

vlan#name (name it what you want)

vlan#exit

fig#int f#/#

-To an end point-

if#sw mod access

if#sw acc vlan 10

-to the router/mls-

if#sw mod trunk

----------------------------------------------------------------------------------------------------

On the multi layer switch (distribution layer)

\>en

#conf t

-it's so common to forget to identify the vlans before routing them which would result in the process not working-

fig#vlan 10

vlan#exit

fig#vlan 20

vlan#name (name it what you want)

vlan#exit

fig#int vlan 10

if#ip address 192.168.0.1 255.255.255.252

if#exit

fig#int vlan 20

if#ip address 192.168.0.5 255.255.255.252

if#exit

fig#ip routing
