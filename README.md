# gosafely
Go Client API for SendSafely

## Install

```
go install github.com/stephendotcarter/gosafely/cmd/gosafely
```

## Configure

Export the following variables:

```
export SS_API_URL='MY_SENDSAFELY_URL'
export SS_API_KEY_ID='MY_SENDSAFELY_ID'
export SS_API_KEY_SECRET='MY_SENDSAFELY_SECRET'
```

*Note: Details on [Obtaining an API Key and API Secret](https://sendsafely.zendesk.com/hc/en-us/articles/204583665-Obtaining-an-API-Key-and-API-Secret).*

## Usage

- Show files for a given URL:
  ```
  gosafely list -u https://sendsafely.test.com/receive/?thread=ABCD-EFGH&packageCode=11aa22bb33cc#keyCode=dd44ee55ff66

  Package | 11aa22bb33cc
  Sent by | user1@test.com
  Sent on | Oct 31, 2018 6:22:37 PM

  +---+---------------------------+--------+-----------+
  | # |         UPLOADED          |  SIZE  | FILE NAME |
  +---+---------------------------+--------+-----------+
  | 0 | Wed Oct 31 at 18:22 (GMT) | 5.1 MB | 5mb.dat   |
  +---+---------------------------+--------+-----------+
  ```
- Download files for a given URL:

  ```
  $ gosafely download -u https://sendsafely.test.com/receive/?thread=ABCD-EFGH&packageCode=11aa22bb33cc#keyCode=dd44ee55ff66

  Package | 11aa22bb33cc
  Sent by | user1@test.com
  Sent on | Oct 31, 2018 6:22:37 PM

  +---+---------------------------+--------+-----------+
  | # |         UPLOADED          |  SIZE  | FILE NAME |
  +---+---------------------------+--------+-----------+
  | 0 | Wed Oct 31 at 18:22 (GMT) | 5.1 MB | 5mb.dat   |
  +---+---------------------------+--------+-----------+
  Files 0

  Downloading 5mb.dat
  5.1 MB/5.1 MB                      
  ```
  *Note: Download multiple files by providing comma seaparated list of file numbers.*

- Files are downloaded to the current directory:
  ```
  $ ls -lh
  total 4.9M
  -rw-r--r-- 1 stephen stephen 4.9M Nov  4 22:51 5mb.dat
  ```
