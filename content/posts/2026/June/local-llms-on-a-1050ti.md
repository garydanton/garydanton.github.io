+++
date = '2026-06-19T08:44:01+01:00'
draft = false
title = 'Running Local LLMs on a NVIDIA 1050Ti'
categories = ["technology"]
+++

> "Just because you could do it, doesn't mean you should do it." - Ian Malcolm, Jurassic Park

As mentioned in my recent [Homelab Overview](/posts/2026/june/homelab-june-2026/) I've currently got a Dell Optiplex 3050 running Jellyfin sitting in my rack. This is doing a sterling job hosting my small media collection around the house, but it's sitting idle for at least 90% of the time.

I've previously spent some time running Ollama when it was first launched on an old gaming PC, but always seemed to run into driver issues. Now I have a working setup with the correct NVIDIA drivers for Linux - let's throw OLMega at one of the lowest-spec GPU's around!

## Installing and Running Ollama

Installing Ollama on the Optiplex is a piece of cake.

SSH into the server, run the usual update cycle:

```sudo apt update && sudo apt upgrade -y```

Then pull Ollama using the following command:

```curl -fsSL https://ollama.com/install.sh | sh```

This pull's Ollama and takes care of any dependancies, after a few minutes it all installed.

## Picking an LLM

Given that the 1050Ti installed in my media server has a paltry 4GB of VRAM, I'm very limited in what I can run.

I've chosen to test this setup with with Meta's [llama3.2 LLM](https://ollama.com/library/llama3.2), specifically the 3B model. In theory this is a good general purpose model, that should give reasonable performance on this hardware.

This can be pulled via the following command:

```ollama run llama3.2:3b```

I fed the terminal a few prompts and everything seems to be surprisingly responsive. I, however, want to benchmark this against other models, so I need a consistent test.

## Benchmarking the 1050Ti

After some research, the classic [Fox, Geese and Grain puzzle](https://en.wikipedia.org/wiki/River_crossing_puzzle) was recommended as a benchmark. In order to turn on some logging, you need to start Ollama using the --verbose flag, so in my case:

```ollama run llama3.2:3b --verbose```

I fed Ollama the following prompt:

```"A farmer needs to cross a river with a fox, a goose, and a bag of grain. The boat can only hold the farmer and one item at a time. If the fox is left alone with the goose, the fox will eat it. If the goose is left alone with the grain, the goose will eat it. How does the farmer get everything across the river?"```

This outputted:

---

```

"This classic problem is known as the "Fox, Goose, and Grain" puzzle. 
Here's a step-by-step solution to get everything across the river safely:

1. Farmer takes the goose across the river first and leaves it on the 
other side.
2. The farmer goes back to the original side and picks up the grain.
3. The farmer takes the grain across the river, but he doesn't leave it 
with the goose. Instead, he leaves it on the other side with the goose.
4. Now, the farmer goes back to the original side and picks up the fox.
5. The farmer takes the fox across the river, but again, he doesn't leave 
it with the goose or grain. He leaves it on the other side with the grain.
6. Finally, the farmer goes back to the original side and picks up the 
goose.
7. The farmer takes the goose across the river, this time leaving it alone 
without the grain.

The sequence of steps is crucial in solving the puzzle, as it ensures that 
no two problematic animals (fox and goose) are left together at any point 
during the crossing process.

By following these steps, the farmer can safely transport all three items 
(the fox, the goose, and the bag of grain) across the river."

```

---

With the logs giving me the following stats:

| **Category** | **Value** |
| --- | --- |
| Total Duration | 10.867172475s |
| Load Duration | 234.770063ms |
| Prompt Eval Count | 231 token(s) |
| Prompt Eval Duration | 287.518ms |
| Prompt Eval Rate | 803.43 tokens/s |
| Eval Count | 258 token(s) |
| Eval Duration | 10.342666s |
| Eval Rate | 24.95 tokens/s |

While not terribly useful on its own, this will give me a good gauge moving forwards.

## Thoughts

Overall, I'm genuinely surprised at how responsive this LLM and GPU combo is - everything seems quick and snappy, and the user experience is good. I'll admit I'm only scratching the surface of this model and I'll be playing around with it over the coming weeks, but it's promising.

I like the idea of using small models on low-end hardware for specific tasks rather than the expensive, subscription-based model that the industry has been embracing over the last decade.