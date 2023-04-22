i到ChatGPT官网 登录

![请添加图片描述](https://img-blog.csdnimg.cn/fedbe06664e74bdbbb9533742b419237.png)

![请添加图片描述](https://img-blog.csdnimg.cn/d8808d650eeb48988d73916b7a31980e.png)

![请添加图片描述](https://img-blog.csdnimg.cn/41b72ed4b9e94231ae544c5f49d45797.png)

保存这个key
然后去google搜索colab

![请添加图片描述](https://img-blog.csdnimg.cn/c27354df900b452c95b6cd52eeb7cb32.png)


![请添加图片描述](https://img-blog.csdnimg.cn/7da43bd30f58445792d5fe50bc95d33c.png)


```
pip install openai
```

```
import openai

API_KEY = '你的OpenAIkey'    
openai.api_key = API_KEY
model_id = 'gpt-3.5-turbo'

def ChatGPT_conversation(conversation):
    response = openai.ChatCompletion.create(
        model=model_id,
        messages=conversation
    )
    # api_usage = response['usage']
    # print('Total token consumed: {0}'.format(api_usage['total_tokens']))
    # stop means complete
    # print(response['choices'][0].finish_reason)
    # print(response['choices'][0].index)
    conversation.append({'role': response.choices[0].message.role, 'content': response.choices[0].message.content})
    return conversation

conversation = []
conversation.append({'role': 'system', 'content': 'How may I help you?'})
conversation = ChatGPT_conversation(conversation)
print('{0}: {1}\n'.format(conversation[-1]['role'].strip(), conversation[-1]['content'].strip()))

while True:
    prompt = input('User:')
    conversation.append({'role': 'user', 'content': prompt})
    conversation = ChatGPT_conversation(conversation)
    print('{0}: {1}\n'.format(conversation[-1]['role'].strip(), conversation[-1]['content'].strip()))

```


# 直接使用chatBox
[gitHub-chatBox](https://github.com/Bin-Huang/chatbox/releases)
