# GPT2-Chinese-Gulong

## Description

自从[GPT2-Chinese](https://github.com/Morizeyao/GPT2-Chinese)开源模型提出以来，涌现了很多基于此的有趣模型。本项目收到LEE Meng的[直觀理解 GPT-2 語言模型並生成金庸武俠小說](https://leemeng.tw/gpt2-language-model-generate-chinese-jing-yong-novels.html)
一文启发，文中GPT2被证明能够较好地学习到金庸的风格并生成较为通顺的续写。金古二人并为当代武侠巨擘，但两人的写作风格大相径庭。金庸重形，古龙重意。本项目旨在尝试GPT2是否能用于生成古龙式武侠小说。

Since the [GPT2-Chinese](https://github.com/Morizeyao/GPT2-Chinese) was published, many interesting models based on it have emerged. This project is inspired by LEE Meng's [article](https://leemeng.tw/gpt2-language-model-generate-chinese-jing-yong-novels.html), in which GPT2 
is proved able to learn Jin Yong's writing style and generate a rather reasonable context given an input prefix. Jin Yong and Gu Long are both contemporary Wuxia novel giants, 
but their writing styles are very different. Jin Yong is more focused on the storyline, while Gu Long is more focused on the spirit. This project aims to examine whether GPT2 can be used to generate Gu Long style Wuxia context.

## Data&Training

训练数据是共计9.4MB的十本古龙小说，包含绝代双骄、武林外史、小李飞刀系列（共五本)以及楚留香系列（共三本）。一共有461个章节，约378万字被提取用于训练。训练在Google Colab上完成，参数如下：batch_size=3, gradient_accumilation=2, lr=1e-4, epochs=40.

The training data are ten novels of Gu Long, and the data volume is 9.4MB. There are 461 chapters and around 3780 thousand Chinese characters in total. The training was done on Google Colab with batch_size=3, gradient_accumilation=2, lr=1e-4, epochs=40.

## Results&Discussion

给定上文是“*她的匕首此刻就架在他的咽喉上，只要稍一用力气*”，生成的样例如下：

* 例1：*她的匕首此刻就架在他的咽喉上，只要稍一用力气，他就会倒下去。他的手已握住了他的脉，眼睛里充满了惊讶和怀疑和怀疑。他的确已无法再戴上这种感觉，他实在不忍看。“你不该放下她？”“我还是很感激你？”“我不能。”“那么你就算杀了我，也不会放过你，但我们是如此，还要看你一眼的男人，我就算杀了你也没关系。”“你现在还不配？”“我迟早总是要看你的，你已是个老人，你难道还不满意？”“不错，我的确看错了，可是我对你也看不出。”他的确像是个完全看不出来的人，可以感觉到他的女人在笑，他的笑容忽然变得说不出的诡秘。这种感觉就像是冰山般消失在他身上，他的心一直都*

* 例2：*她的匕首此刻就架在他的咽喉上，只要稍一用力气，就可以解脱，你的本事就非但不能反抗，也不能还手。”楚留香道：“为什麽？”南宫灵道：“你要我放了她。”楚留香讶然道：“那只因你已没有力气去对她了。”南宫灵大笑道：“我知道你是个很会平凡的人，我若是你，她也会这么样做的，那就是你，我的人难道从来没有把握能杀死你么？”楚留香长长叹息了一声，道：“我有时真的，希望你不会杀她的，你只要能杀得死我，就不会杀我十分她的。”南宫灵扭转了头，目中忽然露出幽怨之色，缓缓道：“我难道真的没有杀死你？”楚留香握紧双拳，指节都已停止，他既没有说一句话，也没有阻拦，因为*

* 例3：*她的匕首此刻就在他的咽喉上，只要稍一用力气，就休想再活下去。谁知就在这时，突听“砰”的一响，竟又是“嗖”的一响，接着“咔嚓”一声，火星四射了进来。这一片火光，正是一片黑暗，天地间的荒坟墓。小鱼儿不觉奇怪，暗道：“这究竟是怎么回事？”这人的语声，竟似真的是慕容九妹。小鱼儿不禁暗暗叹息：“他为什么要救他？为什么不说？”这人的语声，竟似有许多人难测的，而小鱼儿的手，竟和慕容九妹在一起。小鱼儿暗笑忖道：“不错，这人是谁？”这人不但慕容九妹与慕容九妹见面面面，却是慕容九妹的。小鱼儿也瞧不见她说的是什么人，心念一转，转头去瞧那“小鱼儿”就走，慕容*

可以看出，模型（有时）能够推断出匕首刺进咽喉的结果是“倒下去”、‘解脱’或者“休想再活下去”。例1和例2显示了模型一定程度上学到了古龙式的人物对话，尤其是男女之间的恩怨情仇，例3里模型则学会了在生死攸关的情节给出了一个转折。

生成文本的质量总的来说差强人意。考虑这次训练集的规模不算很大，如果将古龙全集用于训练，应该可以有更好的结果。

Given the prefix "*Her dagger was at his throat at the moment, and with the slightest effort*", the resulting samples are as follows.

* Sample 1: *Her dagger was at his throat at the moment, and with the slightest effort he would fall. His hand had taken hold of his pulse, and his eyes were filled with surprise and doubt and suspicion. It was true that he could no longer wear the feeling, and he could not bear to look at it. "You should not give up on her?" "I'm still grateful to you?" "I can't." "Then you will not be spared even if you kill me, but we are like so, a man who still looks at you, I do not care if I kill you." "You are not worthy now?" "Sooner or later I always have to look at you, you are already an old man, are you still not satisfied?" "Sure, I did look at you wrong, but I can't see anything in you either." He did seem like a man who could not be seen through at all, could feel his woman smiling, and his smile suddenly became indescribably secretive. This feeling disappeared from him like an iceberg, and his heart kept*

* Sample 2: *Her dagger was at his throat at the moment, and with the slightest effort, there would be a relief, your skills will not only be unable to resist but also can not fight back." Chu Liuxiang said: "Why?" Nangong Ling said: "You want me to let her go." Chu Liuxiang was surprised: "That's only because you have no more strength for dealing with her." Nangong Ling laughed and said: "I know you are a very ordinary person, if I were you, she would also do the same, that is you, aren't my people sure they can kill you?" Chu Liuxiang a long sigh, said: "Sometimes I really hope you will not kill her, if you could just kill me, will not kill me very her." Nangong Ling twisted his head, the eyes suddenly showed a sorrowful color, slowly said: "Didn't I really kill you?" Chu Liuxiang clenched both fists, knuckles have stopped, he neither said a word nor blocked, because*

* Sample 3: *Her dagger was at his throat at the moment, and with the slightest effort, he would not be alive anymore. No one could have anticipated that at this moment, there was suddenly a "bang", but also a "whoosh", then a "click", sparks shot in. This piece of fire, is darkness, the desolate grave between heaven and earth. Xiao Yuer felt strange, thinking in mind: "What the hell is going on here?" This person's voice sounds like Murong Jiumei, Xiao Yuer couldn't help but secretly sigh: "Why did he want to save him? Why didn't he say so?" This person's voice actually seems to have many people difficult to predict, and Xiao Yuer's hand and Murong Jiumei's hand were actually holding together. Xiao Yuer secretly smiled and thought: "Good, who is this person?" This person not only Murong Jiumei and Murong Jiumei meet face to face, but Murong Jiumei. Xiao Yuer also can not see the person she was talking about, he thought about it again, turn his head to see that "Xiao Yuer" and go, Murong*

It can be seen that the model is (sometimes) able to infer that a dagger in the throat results in "fall", "relief", or "not be alive anymore". Examples 1 and 2 show that the model has learned a certain degree of Gurung-style character dialogue, especially when it comes to the feud between a man and a woman, while in example 3 the model has learned to give a twist in a life-and-death situation. 

The quality of the generated text is barely satisfactory. Considering the size of the training set is relatively small this time, we can expect better results if the complete works of Gu Long are used for training.


## Conclusion

GPT2在长文本生成方面确实有这不俗的表现。通过用古龙的小说训练GPT2，我们得到了可以以古龙风格进行仿写的模型。但是生成的文本还是较为生硬，不能以假乱真。下一步是用更大的数据集和更先进的模型进行测试，比如[CPM](https://github.com/TsinghuaAI/CPM-1-Generate)。

GPT2 does have a notable performance in long text generation. By training GPT2 on Gu Long's novels, we obtained a model that can imitate Gu Long's writing style. However, the generated text is still relatively rigid and cannot fool humans. Future works include further testing with a larger dataset and a more advanced model, such as [CPM](https://github.com/TsinghuaAI/CPM-1-Generate).

## Model

模型可在[此处](https://huggingface.co/1one5ome/gpt2-chinese-gulong)下载。

Please download the model [here](https://huggingface.co/1one5ome/gpt2-chinese-gulong) if interested.
