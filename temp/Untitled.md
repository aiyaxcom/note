curl --location 'http://gateway:8080/openai/v1/chat/completions' \
--header 'Content-Type: application/json' \
--data '{
    "model": "gpt-3.5-turbo",
    "messages": [{"role": "system", "content": "请介绍一下chatgpt"}, {"role": "user", "content": "你好,世界"}],
    "stream": false
  }'

https://test.aijox.com/openai/v1/models