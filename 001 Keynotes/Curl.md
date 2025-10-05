`Client URL` a CLI to transfer data.

### Flags:
- `-o` : output to a file.
- `-X <GET/POST/HEAD...>` : Gets data in that HTTP request method.
- `-i`: prints the metadata / header of the response.
- `-v`: gets even more data about the request.
- `--location`: gets all the redirection done to fetch the response.
- `-O`: saves the file on disk.
- `-C -`: resumes download that is previously stopped.
### Commands:
- `curl --get <url>`: fetches the url and prints the contents.
- `curl --head <url>`: fetches the url and prints the contents and the header.