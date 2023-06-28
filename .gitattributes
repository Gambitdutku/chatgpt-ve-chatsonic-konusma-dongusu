import openai
import requests

openai.api_key = 'API ERİŞİM KODU'  #Mallesef artık ücretsiz verilmiyor
from writesonic import ChatSonicAPI


api_key = "API eriişim kodu" # bu da ücretli
api_secret = "API_şifresi"

chatsonic = ChatSonicAPI(api_key, api_secret)

def generate_response(prompt):
    response = openai.Completion.create(
        engine='text-davinci-002',
        prompt=prompt,
        max_tokens=50,  #mesaj uzunluğunu belirler uçuk rakamlar girmeyin cevap vermesi çok uzun sürebilir ya da vermeyebilir 
        temperature=1, # risk oranı 1 olunca en uçuk saçma sapan şeyleri söyleyebilir 0 olunca en riskiz yanıtları verir 
        n=1, #yanıt sayısı yükseltmeyin döngü sapıtıyor
        stop=None #gerçekten açıklamama gerek var mı
    )
    return response.choices[0].text.strip()

def chat_with_models(prompt, depth):
    response = generate_response(prompt)

    if depth == 0:
        print("ChatGPT:", response)
        return

    print("ChatGPT:", response)

    chat_with_models(response, depth - 1)

def chat_screen():
    print("ChatGPT: Merhaba! Size nasıl yardımcı olabilirim?") # bu kısım sizin girdi girebilmeniz için 
    user_input = input("Siz: ")

    while user_input.lower() != "quit":
        response = chatsonic.generate_text(user_input)
                                json={'prompt': user_input}).json()
        chat_with_models(response['completion'], 'istediğiniz döngü sayısı') # sınırısız çalıştırırsanız openai api keyi geçersiz kılıyor
        user_input = input("Siz: ")

chat_screen()

