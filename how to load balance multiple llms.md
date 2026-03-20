---
created: 2026-03-20T15:52:35+08:00
modified: 2026-03-20T16:11:44+08:00
---

# how to load balance multiple llms

qwen3.5:35b seems to fit nicely in a single v100 32g.

consider run with eight ever-lasting ollama docker containers.

route request to the least busy backend, you can view the gpu util separately. run gpu util check per container docker exec?

---

we might probe for model liviness by sending hello world constantly to a model endpoint, see if it works well. or just run a small gpu test inside the container. normal gpu memory allocation, multiplication in torch etc. any specific tool that we can use to test the usability of a single gpu?

---

about stability:

try to install different version of cuda drivers, ollama versions, models, on different machines. be scientific, find the most stable one using the same prompt and same temperature setting (temp=0)

you had better to use temp=0 to get the shortest response first, tune your query.
