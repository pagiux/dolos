# DOLOS
*Merging Moving Target Defense and Cyber Deception*


`DOLOS` (from Δόλος "Deception", the spirit of trickery). `DOLOS` is a novel architecture that unifies Cyber Deception and Moving Target Defense approaches. `DOLOS` is motivated by the insight that deceptive techniques are much more powerful when integrated into production systems rather than deployed alongside them. `DOLOS` combines typical Moving Target Defense techniques, such as randomization, diversity, and
redundancy, with cyber deception and seamlessly integrates them into production systems through multiple layers of isolation. 



### Installing

    An easy-to-use CMakeLists.txt is provided.
	
### Usage

The moving target defense tools are configured using an `dolos.conf` file with JSON format. Example:

	{
		"tool_1": {
			"file": "Portspoof",
			"class": "Portspoof",
			"method": "start",
			"ports": [4444]
		}

		"tool_2": {
			"file": "Tcprooter",
			"class": "Tcprooter",
			"method": "start",
			"ports": [5000]
		}
	}
	
Inside the `test` directory, for each supported OS distribution, there is a `Dockerfile` to test `DOLOS` (for the moment there is only the Linux version).

**In order to test the DOLOS Agent using a Docker container**: 

* **put** inside `test/agent` the compiled binary, the tools and the configuration file
* **build** Docker Image `docker build -t agent .`
* **parse** AppArmor rules `apparmor_parser -r -W docker-network`
* **run** the container `docker run --rm -it -p 4444:4444 -p 5000:5000 --security-opt apparmor=docker-network agent`

### License

`DOLOS` was made with ♥ and it is released under the GPL 3 license.
