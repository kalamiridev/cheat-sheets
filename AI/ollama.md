## Ollama Windows

### Expose Ollama service to local network

- Allow Ollama port on Firewall

```bash
netsh advfirewall firewall add rule name="Ollama" dir=in action=allow protocol=TCP localport=11434
```

- Add Environment Variable for your Account

  OLLAMA_HOST=0:0:0:0

- Start Ollama service

```bash
ollama serve
```

- Check Ollama port

```bash
netstat -an | findstr 11434
```

- Check Ollama service

```bash
curl http://localhost:11434/api/generate -d '{"model": "llama3", "prompt": "Hello"}'
```
