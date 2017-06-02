# nagios-plugin-influxdb-data
Nagios plugin to check if a measurement received new values in a the last given seconds.

E.g. check if a measurement received values in the last 2 hours (for knowing that the message broker and sensor delivers data for example.)

## Authors

Andreas Bader <development -(at)- geekparadise.de>

## Usage

    check_influxdb_data <host> <port> <database name> <username> <password> <measurement name> <time in seconds between runs that is not warning> <time in seconds between runs thar is not critical>

## Examples

    $ ./check_influxdb_data 127.0.0.1 8086 testdatabase testuser testpw testmeasurement 3200 7200
    OK: measurement testmeasurement in testdatabase on 127.0.01: has received 5 values in the last 3200 seconds.

     $ ./check_influxdb_data 127.0.0.1 8086 testdatabase testuser testpw testmeasurement  3200 7200
    ERROR: measurement testmeasurement has received 0 values in the last 7200 seconds.

     $ ./check_influxdb_data 127.0.0.1 8086 testdatabase testuser testpw testmeasurement  3200 7200
    WARNING: measurement testmeasurement has received 0 values in the last 3200 seconds.