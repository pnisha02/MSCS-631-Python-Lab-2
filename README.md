# Python Lab 2: UDP Pinger

**Student:** Nisha Patel  
**Course:** MSCS 631 B01: Advanced Computer Networks  
**Instructor:** Dax Bradley  
**Institution:** University of the Cumberlands  

## Lab Objective

This lab demonstrates UDP socket programming in Python. The client sends
10 ping messages to a server, waits up to one second for each response,
and displays either the reply and round-trip time (RTT) or
“Request timed out.” It also calculates packet loss and RTT statistics.

## Project Files

| File or Folder | Description |
|---|---|
| `UDPPingerClient.py` | Client program that sends pings and reports results |
| `UDPPingerServer.py` | Instructor-provided server that simulates packet loss |
| `START_SERVER.bat` | Windows shortcut for starting the server |
| `RUN_CLIENT.bat` | Windows shortcut for running the client |
| `Python Lab 2.docx` | Two-paragraph reflection with a reference |
| `screenshots/SS1_Client_Output.png` | Screenshot showing all 10 ping results and final statistics |
| `README.md` | Project description and run instructions |

## Requirements

- Python 3
- Two Command Prompt windows
- No additional Python packages are required

## How to Run

Extract the ZIP folder before running the programs.

### Option 1: Windows Batch Files

1. Double-click `START_SERVER.bat`.
2. Leave the server window open. A blank waiting window is normal.
3. Double-click `RUN_CLIENT.bat`.
4. Wait for all 10 pings and the final statistics.
5. Press `Ctrl+C` in the server window when finished.

### Option 2: Command Prompt

Open Command Prompt inside the project folder and start the server:

```bat
py UDPPingerServer.py
```

Open a second Command Prompt in the same folder and run the client:

```bat
py UDPPingerClient.py
```

If `py` is unavailable, replace it with `python`.

## Program Behavior

- Uses IPv4 UDP sockets.
- Sends messages in the format `Ping sequence_number timestamp`.
- Numbers the messages from 1 through 10.
- Uses `127.0.0.1` and port `12000` for localhost testing.
- Waits up to one second for each matching response.
- Displays the server’s uppercase reply and RTT in seconds.
- Displays “Request timed out” when no matching reply arrives in time.
- Reports sent, received, and lost packets, plus packet loss percentage.
- Reports minimum, maximum, and average RTT for successful replies.

## Results from My Localhost Test

| Measurement | Result |
|---|---|
| Packets sent | 10 |
| Replies received | 4 |
| Packets lost | 6 |
| Packet loss | 60.0% |
| Minimum RTT | 0.000163 seconds |
| Maximum RTT | 0.000583 seconds |
| Average RTT | 0.000317 seconds |

Successful replies were received for pings 1, 2, 6, and 9.
Pings 3, 4, 5, 7, 8, and 10 timed out.

The server randomly ignores some requests, so results vary between runs.
The observed 60% loss represents this particular test. It does not indicate
that every run will have the same loss rate.

Both programs ran on the same computer, so these RTT values describe
localhost communication.

## Screenshot Evidence

The file `screenshots/SS1_Client_Output.png` shows:

- All 10 ping attempts
- Successful uppercase replies
- RTT values in seconds
- Timeout messages
- Final packet-loss and RTT statistics

One screenshot contains the complete output for this run.

## Testing on Different Computers

After localhost testing:

1. Run the server on another computer on a reachable network.
2. Find that computer’s IPv4 address.
3. From the client computer, run:

```bat
py UDPPingerClient.py SERVER_IPV4_ADDRESS
```

Replace `SERVER_IPV4_ADDRESS` with the server computer’s actual address.
The server must be running, and its firewall must permit UDP traffic on
port 12000.

The results documented above are from localhost testing only.

## Troubleshooting

- **All requests time out:** Confirm that the server is running and that
  the client uses the correct address and port.
- **Some requests time out:** This is expected because the server
  deliberately simulates packet loss.
- **Port already in use:** Stop any previous server instance before
  starting another.
- **Python command is not recognized:** Confirm that Python is installed
  and try `python` instead of `py`.

## Submission Contents

The submission includes the complete client source code, the client-output
screenshot, and the two-paragraph reflection in `Python Lab 2.docx`.
The supplied server, batch files, and this README are included to make
the program easy to run.

## Reference

Python Software Foundation. (n.d.). *socket—Low-level networking interface*.
Python documentation. https://docs.python.org/3/library/socket.html
