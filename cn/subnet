def get_octet1(ip):
    octet1 = ""
    i = 0
    while ip[i] != '.':
        octet1 += ip[i]
        i += 1
    octet1_asint = int(octet1)
    return octet1_asint


def get_class(octet1):
    class_range = [127, 191, 223, 239, 255]
    i = 0
    while octet1 > class_range[i]:
        i += 1
    return chr(65 + i)


def get_def_subnet(Class):
    null_octets = ord(Class) - 65 + 1
    def_subnet = ""

    for i in range(32):
        if i % 8 == 0 and i != 0:
            def_subnet += '.'
        def_subnet += '0'

    for i in range((8 * null_octets) + null_octets):
        if def_subnet[i] == '0':
            def_subnet = def_subnet[:i] + '1' + def_subnet[i + 1:]

    return def_subnet


def dec_to_bin(host):
    bin_no = 0
    i = 1
    while host > 0:
        bin_no += (host % 2) * 10**i
        host //= 2
        i += 1
    return bin_no // 10


def net_id_gen(ip):
    net_id = ""
    dots = 0
    for i in range(len(ip)):
        net_id += ip[i]
        if ip[i] == '.':
            dots += 1
        if dots == 3:
            break
    return net_id


def main():
    ip = input("Enter ip address: ")
    host = int(input("Enter no. of hosts: "))

    Octet1 = get_octet1(ip)

    Class = get_class(Octet1)
    def_bin_sn = get_def_subnet(Class)

    res_bits = len(str(dec_to_bin(host)))
    SG = 2 ** res_bits

    net_id = net_id_gen(ip)
    length = 256 // SG

    for i in range(length):
        first = net_id + str(i * SG)
        last = net_id + str(((i + 1) * SG) - 1)
        print(first, "-", last)

main()
