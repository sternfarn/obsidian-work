
- [ ] Make work with localhost. does not work with localhost since same domain is not true, right?
- [ ] Report ai.nexxar.com CORS security risk and add the same time allow my app, both to get the token and to chat, ask claude again.

## Response examples

- **Action known, data unknown:** response_format: { type: 'json_schema', … }
- **Action unknown, or several actions in sequence:** tool use

vercel sdk, but better handwritten, not much code.

https://ai.nexxar.com/ollama/v1/chat/completions
https://ai.nexxar.com/openai/chat/completions

## Prose

```json
{
  "id": "gpt-oss:20b-1c5b4c2f-1145-4a48-ba9d-44e09c973a33",
  "created": 1788446677,
  "model": "gpt-oss:20b",
  "choices": [
    {
      "index": 0,
      "logprobs": null,
      "finish_reason": "stop",
      "message": {
        "role": "assistant",
        "content": "en: Revenue  \nde: Umsatz",
        "reasoning_content": "User wants \"a new column for revenue\" and says languages: en, de. So we need to provide table column titles in each requested language: English and German. Likely output as separate lines or pairs.\n\nThey want the title of a new column that would represent revenue. In English maybe \"Revenue\", \"Total Revenue\". In German maybe \"Umsatz\", \"Gesamtumsatz\".\n\nWe could ask for clarification? No, we can provide likely appropriate titles.\n\nGiven they didn't specify format, I'll give two lines:\n\nen: Revenue\n\nde: Umsatz\n\nAlternatively if more formal: en: Total Revenue; de: Gesamter Umsatz. But simpler is fine.\n\nI'll produce two separate lines: \"en: Revenue\" and \"de: Umsatz\"."
      }
    }
  ],
  "object": "chat.completion",
  "usage": {
    "input_tokens": 100,
    "output_tokens": 169,
    "total_tokens": 269,
    "prompt_tokens": 100,
    "completion_tokens": 169,
    "response_token/s": 179.56,
    "prompt_token/s": 587.7,
    "total_duration": 7158593258,
    "load_duration": 6039543684,
    "prompt_eval_count": 100,
    "prompt_eval_duration": 170154000,
    "eval_count": 169,
    "eval_duration": 941169000,
    "approximate_total": "0h0m7s",
    "completion_tokens_details": {
      "reasoning_tokens": 0,
      "accepted_prediction_tokens": 0,
      "rejected_prediction_tokens": 0
    }
  }
}

```

## Json

```json
{
  "id": "gpt-oss:20b-7b92ad8c-25fc-4040-9447-630e9f054964",
  "created": 1788446740,
  "model": "gpt-oss:20b",
  "choices": [
    {
      "index": 0,
      "logprobs": null,
      "finish_reason": "stop",
      "message": {
        "role": "assistant",
        "content": "{ \"en\": \"Revenue\", \"de\": \"Umsatz\" }",
        "reasoning_content": "The user says: \"A new column for revenue. Languages: en, de.\" The developer instruction: \"Give the table column title in each language the user asks for.\"\n\nSo they want a table column title presumably? They want a column titled \"Revenue\" in English and German? Likely \"Revenue\" is English; \"Umsatz\" is German (or \"Einnahmen\"). The phrase \"new column for revenue.\" They want the table column titles. So output something like:\n\nen: Revenue\nde: Umsatz\n\nProbably just give them separate lines. They may want a small table or simple list. The instruction says give the table column title in each language asked.\n\nThus I will produce:\n\nEnglish: Revenue  \nGerman: Umsatz  \n\nor in a more succinct format: en: Revenue | de: Umsatz. \n\nBetter to keep plain text. I think that is enough."
      }
    }
  ],
  "object": "chat.completion",
  "usage": {
    "input_tokens": 287,
    "output_tokens": 17,
    "total_tokens": 304,
    "prompt_tokens": 287,
    "completion_tokens": 17,
    "response_token/s": 156.53,
    "prompt_token/s": 10792.31,
    "total_duration": 1590747065,
    "load_duration": 305228314,
    "prompt_eval_count": 287,
    "prompt_eval_duration": 26593000,
    "eval_count": 17,
    "eval_duration": 108605000,
    "approximate_total": "0h0m1s",
    "completion_tokens_details": {
      "reasoning_tokens": 0,
      "accepted_prediction_tokens": 0,
      "rejected_prediction_tokens": 0
    }
  }
}

```

## Lynx-dev add column

```json
{
    "content": "",
    "toolCalls": [
        {
            "index": 0,
            "id": "call_60ed05qh",
            "type": "function",
            "function": {
                "name": "add_column",
                "arguments": "{}"
            }
        }
    ]
}
```





## Next steps

Verdict: structurally on track. Fix the parse, fix the properties shape, move required up a level, turn the two constants into factories, and align the descriptions — then you'll have seen every mechanical piece of single-turn tool calling. The only concept left after that is feeding the result back as a role: 'tool' message so the loop closes.


