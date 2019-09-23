# NAME

check\_hp\_j4680 - check the status of an HP Officejet J4680 series printer

# USAGE

**check\_hp\_j4680** **-H** _host_ **-f** _function_…

# DESCRIPTION

**check\_hp\_j4680** checks the status of several properties of an HP Officejet
J4680 series printer. To be used as a [Nagios plugin](https://exchange.nagios.org/directory/Plugins/Printing/check_hp_j4680/details)

# REQUIRED ARGUMENTS

The host 

# OPTIONS

- ** -?, -h, --help**

    Show help

- ** -v, --verbose**

    Be more verbose

- **--version**

    Show version and license

- **--function**

    Check for function:

    - black: Percentage of ink left in the black cartridge, value between 0
    and 100, defaults warning 10 critical 1
    - color: Percentage of ink left in the tri-color cartridge, value between
    0 and 100, default warning 10 critical 1
    - pages: Total Page Count of the pages the device has printed in it's
    lifetime, defauls warning 9000 critical 10000
    - status: Ready or not
    - signal: WiFi signal strength, 1 is worst, 5 is best, defaults warning 4
    critical 1

# DIAGNOSTICS

- Could not retrieve page '%s' to get data
(E) The HTML page containing the data could not be retrieved from the host
- Could not get data from page '%s' for function '%s'
(E) The HTML page containing the data could be retrieved from the host but the
requested data was not found on that page
- Unknown function '%s', must be one of black, color, pages, status, signal
(E) The requested function is not supported, must be one of the printer properties
'black', 'color', 'pages', 'status' or the WiFi property 'signal'.

# EXAMPLES

`check_hp_j4680 -H 192.168.0.100 -f black`

# DEPENDENCIES

Perl 5.16.0, Monitoring::Plugin, HTTP::Tiny, List::MoreUtils, Readonly, English

# EXIT STATUS

The exist status is handled by the monitoring interface.

# CONFIGURATION

The default warning and critical thresholds should be overridden by the
standard -w and -c options of the monitoring interface because they depend on
the usage of the device. The defaults thresholds are:

- black 10: 1:
- color 10: 1:
- pages 9000 10000
- signal 4: 1:

# INCOMPATIBILITIES

There are no known incompatibilities but since the data is scraped from pages
in an undefined format, different firmware version could present the data in a
different format which might break things. It is compatible with Firmware
Version `YWM2FN0820BR`.

# BUGS AND LIMITATIONS

The 'ready' function only determines between 'Ready' and not.

Please report any bugs or feature requests at

[Issues for github.com](https://github.com/ipenburg/check_hp_j4680/issues).

# AUTHOR

Roland van Ipenburg, <ipenburg@xs4all.nl>

# LICENSE AND COPYRIGHT

Copyright 2019 by Roland van Ipenburg
This program is free software; you can redistribute it and/or modify
it under the GNU General Public License v3.0.

# DISCLAIMER OF WARRANTY

BECAUSE THIS SOFTWARE IS LICENSED FREE OF CHARGE, THERE IS NO WARRANTY
FOR THE SOFTWARE, TO THE EXTENT PERMITTED BY APPLICABLE LAW. EXCEPT WHEN
OTHERWISE STATED IN WRITING THE COPYRIGHT HOLDERS AND/OR OTHER PARTIES
PROVIDE THE SOFTWARE "AS IS" WITHOUT WARRANTY OF ANY KIND, EITHER
EXPRESSED OR IMPLIED, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE. THE
ENTIRE RISK AS TO THE QUALITY AND PERFORMANCE OF THE SOFTWARE IS WITH
YOU. SHOULD THE SOFTWARE PROVE DEFECTIVE, YOU ASSUME THE COST OF ALL
NECESSARY SERVICING, REPAIR, OR CORRECTION.

IN NO EVENT UNLESS REQUIRED BY APPLICABLE LAW OR AGREED TO IN WRITING
WILL ANY COPYRIGHT HOLDER, OR ANY OTHER PARTY WHO MAY MODIFY AND/OR
REDISTRIBUTE THE SOFTWARE AS PERMITTED BY THE ABOVE LICENSE, BE
LIABLE TO YOU FOR DAMAGES, INCLUDING ANY GENERAL, SPECIAL, INCIDENTAL,
OR CONSEQUENTIAL DAMAGES ARISING OUT OF THE USE OR INABILITY TO USE
THE SOFTWARE (INCLUDING BUT NOT LIMITED TO LOSS OF DATA OR DATA BEING
RENDERED INACCURATE OR LOSSES SUSTAINED BY YOU OR THIRD PARTIES OR A
FAILURE OF THE SOFTWARE TO OPERATE WITH ANY OTHER SOFTWARE), EVEN IF
SUCH HOLDER OR OTHER PARTY HAS BEEN ADVISED OF THE POSSIBILITY OF
SUCH DAMAGES.
