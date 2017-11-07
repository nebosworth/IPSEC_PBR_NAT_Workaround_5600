# IPSEC_PBR_NAT_Workaround_5600

This workaround uses local loopback as an IP for a GRE interface and uses Policy Based Routing (PBR) to get the traffic originating from the IPSEC onto an interface in order to perform NAT functions. 5600 requires traffic be tied to an interface in order to mangle source/dest - in 5400, IPSEC traffic appeared to originate from the interface that the IPSEC was connected on (ie. if IPSEC was over public with a 5400 on the bond1 IP, the traffic was tied to bond1 - 5600 does not tie IPSEC traffic to an interface unless using VTI or GRE).

Traffic enters vRouter via IPSEC, PBR routes the traffic to the tun50 interface (looped back) and NAT transformaton can occur as the traffic comes off of the tun50 interface and back onto the data plane.
