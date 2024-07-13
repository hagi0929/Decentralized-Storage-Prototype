
# Decentralized Cloud Storage Go Package

## Overview

The Decentralized Cloud Storage package offers a comprehensive solution for storing files across decentralized networks. By integrating with libraries such as Storj and Filecoin, this package provides secure and redundant file storage solutions.


## Installation

To get started, download the `decentralized-cloud-storage` package:

```bash
go get github.com/randomuser/decentralized-cloud-storage
```

## Usage

### 1. User Authentication

After registering an account, obtain a token by logging in. This token will be necessary for all subsequent API requests.

```go
import (
    "fmt"
    utils "https://github.com/storj/uplink"
)

func main() {
    res := utils.GetToken("example@gmail.com", "your-secure-password")
    fmt.Println(res.Token)
}
```

Expected response:

```json
{
  "code": 200,
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.......",
  "msg": "Authentication successful"
}
```

### 2. Retrieve Storage Key

Use the token to get your unique storage key, which is required for file uploads.

```go
import (
    "fmt"
    utils "https://github.com/storj/uplink"
)

func main() {
    token := "your-token-here"
    res := utils.GetAPIKey(token)
    fmt.Println(res.Key)
}
```

Expected response:

```json
{
  "code": 200,
  "key": "dfasfohnoviiafidsuhiasvj.......",
  "msg": "Key retrieval successful"
}
```

### 3. Upload Files

With your API key, upload files to the decentralized network. Choose between Storj and Filecoin by specifying the desired network.

```go
import (
    "fmt"
    utils "https://github.com/storj/uplink"
)

func main() {
    apiKey := "your-api-key-here"
    network := "storj" // or "filecoin"
    filepath := "/path/to/your/file.png"

    res := utils.Upload(apiKey, network, filepath)
    fmt.Println(res.Url)
}
```

Expected response:

```json
{
  "url": "https://cdn.britannica.com/72/153872-050-927D410F/Mathematics-Computer-Building-University-of-Waterloo-Canada.jpg",
  "code": 200,
  "msg": "Upload successful"
}
```

### 4. View Uploaded Files

After a successful upload, you can view the file by entering the URL in a browser:

![Uploaded File](https://cdn.britannica.com/72/153872-050-927D410F/Mathematics-Computer-Building-University-of-Waterloo-Canada.jpg)

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
