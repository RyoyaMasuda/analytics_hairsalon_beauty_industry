FROM python:3.9 as builder

RUN apt-get update && apt-get install -y \
    unzip 

# chrome driverのインストール
ADD https://chromedriver.storage.googleapis.com/109.0.5414.74/chromedriver_linux64.zip /opt/chrome/
RUN cd /opt/chrome/ && \
    unzip chromedriver_linux64.zip && \
    rm -f chromedriver_linux64.zip

# pipのアップグレード、requirements.txtのインストール
RUN pip install --upgrade pip
COPY requirements.txt .
RUN pip install --no-cache-dir -r  requirements.txt

FROM python:3.9-slim
COPY --from=builder /opt/ /opt/
COPY --from=builder /usr/local/lib/python3.9/site-packages /usr/local/lib/python3.9/site-packages

RUN apt-get update && apt-get install -y \
    wget \
    curl \
    gnupg

# chrome
RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add && \
    echo 'deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main' | tee /etc/apt/sources.list.d/google-chrome.list && \
    apt-get update && \
    apt-get install -y google-chrome-stable && \
    apt-get -y clean && \
    rm -rf /var/lib/apt/lists/*

ENV TZ="Asia/Tokyo"
RUN echo $TZ > /etc/timezone
