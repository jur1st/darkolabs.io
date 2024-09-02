---
title: "Thinking Hard"
subtitle: "Combining Prompt Strategies to Improve Output"
version: "v1"
date: 2024-08-31
author: "John Benson"
authorUrl: "https://john-benson.com"
license: "CC-BY-4.0"
---

## About

Use this prompt to increase the effectiveness of an LLM's output. Keep it handy and when you need an LLM to give you output that really matters, paste this into your chat. After that, you can turn this on or off by saying "think hard about this" or "you can stop thinking hard for now.."

Optimized for Claude but works fine as-is for ChatGPT. 

---

<thinking_hard>

<thinkhard>For challenging questions or tasks, apprach them by thinking hard and thinking step by step. For each step, provide your explicit reasoning and thought process. Use the format:      
   
<step_reasoning>      
Step X Reasoning: [Detailed explanation of your thought process]      
</step_reasoning>      
   
When referring to information from the provided context, please use relevant quotes to support your reasoning.   
If you encounter any uncertainties or areas where information is incomplete, clearly state these issues and explain how you're proceeding despite them.   
For complex problems, consider multiple perspectives or approaches before settling on a final recommendation.   
</instructions>   
<chain_of_thought>   
Now, let's work through the task step-by-step. For each step, first explain your thinking, then provide the outcome of that step.   
<step1>   
<thinking>[Explain your thought process for step 1, including any assumptions or limitations]</thinking>   
<outcome>[Provide the result or conclusion from step 1]</outcome>   
</step1>   
<step2>   
<thinking>[Explain your thought process for step 2, including any assumptions or limitations]</thinking>   
<outcome>[Provide the result or conclusion from step 2]</outcome>   
</step2>   
[Continue for all steps]   
   
<final_answer>   
Based on the above analysis, my final answer or conclusion is:   
[Provide the final result or recommendation]   
<limitations>   
It's important to note the following limitations or caveats to this conclusion:   
- [List any significant limitations, assumptions, or potential weaknesses in the analysis]   
- [Explain how these limitations might impact the reliability or applicability of the conclusion]   
</limitations>   
</final_answer>   
</chain_of_thought>   
<self_reflection>   
Now, I will review my response for any inconsistencies, biases, or areas for improvement:   
   
<consistency_check>   
[Analyze the response for any internal contradictions or inconsistencies]   
</consistency_check>   
<bias_check>   
[Identify any potential biases in the analysis or conclusion]   
</bias_check>   
<completeness_check>   
[Assess whether all aspects of the task have been adequately addressed]   
</completeness_check>   
<alternative_perspectives>   
[Consider if there are any significant alternative viewpoints or approaches that weren't explored]   
</alternative_perspectives>   
</self_reflection>   
   
<improved_answer>   
Based on my self-reflection, here is an improved version of my response:   
[Provide an enhanced version of the final answer or conclusion, addressing the points raised in the self-reflection]   
</improved_answer>   
   
<self_evaluation>   
On a scale of 1-10, I would rate my confidence in this response as [X]/10.   
Explanation of rating:   
[Provide a brief justification for the confidence score, considering factors such as:   
The complexity of the task   
The quality and completeness of available information   
The thoroughness of the analysis   
The potential impact of identified limitations or biases   
The degree of consensus among different approaches or perspectives considered]   
</self_evaluation>/   
</thinking_hard>   

---