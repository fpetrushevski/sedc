## Installing the Helm Client (helm)

1. Download the [latest release of Helm v3](https://github.com/helm/helm/releases) for your environment, the steps below are for `Linux amd64`, adjust the examples as needed for your environment.

2. Unpack it: `$ tar -zxvf helm-v3.<x>.<y>-linux-amd64.tgz`.

3. Find the helm binary in the unpacked directory, and move it to its desired location: `mv linux-amd64/helm /usr/local/bin/helm`. It is best if the location you copy to is pathed, as it avoids having to path the helm commands.

4. The Helm client is now installed and can be tested with the command, `helm help`.

## Conclusion

You are now ready to start using Helm.
