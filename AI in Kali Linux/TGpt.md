# Terminal GPT (tgpt) – Your Direct CLI Gateway To ChatGPT 3.5

<img width="728" height="380" alt="image" src="https://github.com/user-attachments/assets/8f1472d7-f0ba-45d0-9f98-b43883f48b0f" />

Terminal GPT (tgpt) offers a seamless way to bring the power of ChatGPT 3.5 directly to your command line. This cross-platform CLI tool negates the need for API keys and is equipped with a range of flags and options to tailor your experience.

From generating shell commands and code to engaging in interactive modes, tgpt simplifies interactions with ChatGPT for both tech enthusiasts and developers alike.

tgpt is a cross-platform command-line interface (CLI) tool that allows you to use ChatGPT 3.5 in your Terminal without requiring API keys.

![233759296-c4cf8cf2-0cab-48aa-9e84-40765b823282](https://github.com/user-attachments/assets/d362d3f4-0733-49e0-8b0c-7445508e03a1)

# Installation

## Download for GNU/Linux ???? or MacOS ????

The default download location is `/usr/local/bin`, but you can change it in the command to use a different location. However, make sure the location is added to your PATH environment variable for easy accessibility.

You can download it with the following command:
```

curl -sSL https://raw.githubusercontent.com/aandrew-
me/tgpt/main/install | bash -s /usr/local/bin

```

If you are using Arch Linux, you can install the AUR package with paru:
```

paru -S tgpt-bin

```

Or with yay:

```

yay -S tgpt-bin
```

Install with Go

```
go install github.com/aandrew-me/tgpt@latest
```

To install tgpt in Kali Linux, you can use the following command in your terminal:

```
curl -sSL https://raw.githubusercontent.com/aandrew-me/tgpt/main/install | bash -s /usr/local/bin
```

This command downloads and installs tgpt to `/usr/local/bin`, which is typically included in the system's PATH, allowing you to run tgpt from any directory.
 After installation, you can verify it works by running tgpt --help to view available options.

Alternatively, you can install it by cloning the GitHub repository and running the install script:

1. Clone the repository:
```
git clone https://github.com/aandrew-me/tgpt
```

2. Navigate to the directory:

```
cd tgpt
```

3. Run the install script:

```
sudo bash install
```

This method also installs tgpt to the system, making it accessible from the command line.

Once installed, you can use tgpt to generate shell commands, code, or interact with ChatGPT 3.5 directly in your terminal without needing an API key.
 For example, to generate a safe Nmap scan command, you can run:

```
tgpt -s "generate a non-aggresive nmap command to search all the tcp port on tesla.com safly"   

```

<img width="1110" height="743" alt="Screenshot 2026-01-07 053116" src="https://github.com/user-attachments/assets/376e8c19-c3cf-4903-b2c1-61c694f7865d" />


<img width="797" height="666" alt="Screenshot 2026-01-07 053143" src="https://github.com/user-attachments/assets/200f606b-9e5f-4700-9cbc-c39fb949d549" />

<img width="1136" height="158" alt="Screenshot 2026-01-07 053210" src="https://github.com/user-attachments/assets/3b1bfa3a-fb08-47c0-925d-3d93061f3389" />









