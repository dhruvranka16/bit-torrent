## Bit-Torrent

* Bit-Torrent is a simple command-line torrent client written in Python. It supports both downloading and seeding of `.torrent` files, manages communication with peers, and ensures data integrity by transferring files in pieces.  
* This project is designed for educational purposes to showcase how peer-to-peer (P2P) file-sharing protocols like BitTorrent work behind the scenes.  
* Ideal for anyone interested in networking, distributed systems, or learning the internals of the BitTorrent protocol. The client can be extended with features like UI, encryption, or distributed hash tables (DHT).

## Project Overview :

* **Start:** Run `main.py` via terminal with command-line arguments specifying download or seed mode.  
* **Argument Parsing:** Uses `argparse` and `sys.argv` to process input commands.  
* **Client Initialization:** Creates an instance of the BitTorrent client to manage the session.  
* **Torrent File Processing:** Reads the `.torrent` file to extract metadata including trackers, file info, and piece hashes.  
* **Tracker Communication:** Contacts tracker servers to retrieve a list of peers participating in the swarm.  
* **Peer Swarm Setup:** Establishes connections with available peers.  
* **Mode Selection:** Based on user input, switches to download or seeding mode.

* **Download Mode:**  
  * Creates an empty file ready to receive pieces.  
  * Adds the file handler to the peer swarm and starts downloading.  
  * Requests and downloads pieces from peers.  
  * Validates each piece using hash checks to ensure data integrity.  
  * Writes verified pieces to disk.  
  * Marks download as complete after all pieces are received.

* **Seeding Mode:**  
  * Opens the complete file for reading.  
  * Shares the file with other peers in the network.  
  * Responds to incoming requests for pieces.  
  * Continues seeding to support the swarm.

* After download or seeding, the client continuously handles peer messages such as keep-alives, choke/unchoke signals, and piece availability updates.

## Installation and Build :

* If you don’t have the `pipenv` package installed, install it using the command below, otherwise ignore:  
$ pip3 install pipenv
cpp
Copy
Edit

* Activate the virtual environment and install all required dependencies:  
ruby
Copy
Edit
$ pipenv shell
$ pipenv install --dev


## Run :

* Change directory to `src` inside the Bit-Torrent folder to view help and usage options:  

$ cd src
$ python3 main.py --help


* Example to download a file from a torrent by specifying the destination path:  

$ python3 main.py input_file.torrent -d destination_path/


* Example to seed an existing file by specifying the path to the file:  

$ python3 main.py input_file.torrent -s existing_file_path/


