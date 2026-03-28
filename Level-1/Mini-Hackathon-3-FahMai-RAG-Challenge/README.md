# Mini Hackathon 3 : FahMai RAG Challenge

FahMai (ฟ้าใหม่) is a fictional Thai electronics store. You are given a knowledge base of product pages, store policies, and store information (in Thai). Your task is to build a Retrieval-Augmented Generation (RAG) system that answers 100 multiple-choice questions about the store.

Each question has 10 choices:

- Choices 1-8: content-specific answers
- Choice 9: "ไม่มีข้อมูลนี้ในฐานข้อมูล" (No data available in the knowledge base)
- Choice 10: "คำถามนี้ไม่เกี่ยวข้องกับร้านฟ้าใหม่" (This question is not related to FahMai store)

You MUST use the following ThaiLLMs ONLY:

- OpenThaiGPT-ThaiLLM-8B-instruct-v7.2,
- Pathumma-ThaiLLM-qwen3-8b-think-3.0.0
- Typhoon-S-ThaiLLM-8B-Instruct
- THaLLE-0.2-ThaiLLM-8b-fa

You can access their APIs here, https://playground.thaillm.or.th/chat/

Submit a CSV file with exactly 100 rows:
```
id,answer
1,5
2,3
3,7
...
100,2
```
- id: integer 1-100
- answer: integer 1-10