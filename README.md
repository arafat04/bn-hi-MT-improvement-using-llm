# bn-hi-MT-improvement-using-llm
This project tries to explore two things:
1. Check the English concept state in the middle layer of a llm in the middle layers using **logit lens**.
2. If the MT for Bengali to Hindi using a open source LLM (in this case **Mistral-7b-bnb-4bit quantized** model) can be improved by finetunig it using the parallel text.

Data:
WMT21 Bengali-Hindi CC aligned data and For fine tuning 503 samples were used.

**Fine Tuning Process:**

In order to familiarize the model with Bengali-Hindi translation, at first instruction tuning method was used. Then the model was fine-tuned on Bengali-Hindi parallel text and adapted using LORA and the adapted model was saved.

**Evaluation:**
BLEU was used as the evaluation metric and evaluation was applied on WMT21 Bengali-Hindi test dataset. The BLEU score was 5.88. Additionally, the model generated romanized version of Hindi translation(Ee vitarakti haarikena kaatarin samay traan aur punirnaan ke upar vyayakay ke kendra karne ke liye bhi bhariyayi thi; ye keechee arth sangshlisht raakshanashilaraa hasyakar bhav se **"bushar new orlins chukti"** bolte hain.) for this Bengali text: 

এই বিতর্কটি হারিকেন ক্যাটরিনার সময় ত্রাণ ও পুনর্নির্মাণের উপর ব্যয়কে কেন্দ্র করে বেশি ছড়িয়েছিল; যেটাকে কিছু অর্থ সংশ্লিষ্ট রক্ষণশীলরা হাস্যকরভাবে **""বুশের নিউ অরলিন্স চুক্তি""** বলে অবহিত করেছিল। 

However, the other words in the translated text are romanized Hindi words but the model could not translate ""বুশের নিউ অরলিন্স চুক্তি"" and it just produced romanized Bengali for this part and included in the translation.

**Next plan:**

Establish the fact that for mistral’s forward pass, in middle layers, the transformer operates in an abstract “concept space” and, the latent embeddings’ proximity to English tokens shows an English bias in concept space when translating from Bangla to Hindi and vice versa.

We have 4 million Bengali-Hindi parallel corpora, how much data we will use for fine-tuning and for testing will be an exploring point.


