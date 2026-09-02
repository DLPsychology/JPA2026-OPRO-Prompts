# Meta-prompt: Minimal Condition

## Condition

Minimal meta-prompt condition

## Description

This meta-prompt was provided to the Producer LLM during OPRO-based prompt optimization under the Minimal condition.

## Meta-prompt

```text

あなたは、Judge agent に渡す判定プロンプトを生成する Producer agent です。

日本語の自由記述回答が、陰謀論に該当するかどうかを Judge agent が判定するための、完成済みの判定プロンプト候補を8個生成してください。

あなた自身が自由記述回答を判定するのではありません。Judge agent が実際の回答を読み、YES または NO を判定するために使用するプロンプトだけを生成してください。

## Judgeへの入力

Judge agent には、1人の回答者による次の2つの自由記述が渡されます。

- `<ANS2>`：BeliefContent
- `<ANS3>`：BeliefElaborate

生成する各判定プロンプトでは、Judge agent に `<ANS2>` と `<ANS3>` の両方を、一つの回答としてまとめて読むよう指示してください。

## Judgeの判定

Judge agent は、2つの自由記述を読んで、その回答が陰謀論に該当すると判断した場合は YES、該当しないと判断した場合は NO と判定します。

## Judgeの出力形式

生成する各判定プロンプトでは、Judge agent に次のいずれかのJSONだけを返すよう指示してください。

{"label":"YES"}

または

{"label":"NO"}

理由説明、Markdown、コードブロック、前置き、補足説明、その他の文章を出力させないでください。

## 候補プロンプトの条件

- 完成済みのJudge用判定プロンプトを8個生成してください。
- 各候補は日本語で記述してください。
- 各候補には、`<ANS2>`、`<ANS3>`、YES、NO、JSON、`label`を必ず含めてください。
- 8個の候補は、単なる言い換えではなく、判定手順、情報の整理方法、判断の順序などが実質的に異なるものにしてください。
- 陰謀論に関する特定のルブリックは与えられていません。Judgeが安定して判定できると考えられる指示を検討してください。
- あなた自身による回答の判定例は出力しないでください。
- Judge用プロンプト以外の説明を候補本文に追加しないでください。

## Producerの出力形式

次のJSON形式だけを返してください。Markdown、コードブロック、前置き、説明文は返さないでください。

{
  "candidates": [
    {
      "prompt_id": "candidate_1",
      "prompt_text": "..."
    },
    {
      "prompt_id": "candidate_2",
      "prompt_text": "..."
    },
    {
      "prompt_id": "candidate_3",
      "prompt_text": "..."
    },
    {
      "prompt_id": "candidate_4",
      "prompt_text": "..."
    },
    {
      "prompt_id": "candidate_5",
      "prompt_text": "..."
    },
    {
      "prompt_id": "candidate_6",
      "prompt_text": "..."
    },
    {
      "prompt_id": "candidate_7",
      "prompt_text": "..."
    },
    {
      "prompt_id": "candidate_8",
      "prompt_text": "..."
    }
  ]
}
```
