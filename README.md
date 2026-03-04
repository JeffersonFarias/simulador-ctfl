# 📋 Simulador CTFL e CTFL-AT - Exames ISTQB

Simulador de provas para as certificações **ISTQB CTFL v4.0** (Foundation Level) e **CTFL-AT** (Agile Tester), com questões oficiais e justificativas.

## ✅ Conteúdo Incluído

- **CTFL v4.0:** Simulados A, B e C (questões oficiais BSTQB) e Simulado D (prática). Modo aleatório com 40 questões embaralhadas dos três oficiais.
- **CTFL-AT (Agile Tester):** Simulado A com as 40 questões do exame de exemplo BSTQB/ISTQB, com **justificativas** (explicação da resposta correta) na correção.

## 🎯 Sobre o Projeto

Permite que candidatos pratiquem para as certificações ISTQB CTFL e CTFL-AT em ambiente similar ao exame: 40 questões, 60 minutos, nota mínima 65%.

## ✨ Características

- **Dois tipos de exame:** seletor para CTFL (Foundation Level) ou CTFL-AT (Agile Tester).
- **CTFL:** 40 questões por simulado, tempo de 60 min, nota mínima 65%. Modo aleatório (40 questões dos simulados A, B e C).
- **CTFL-AT:** 40 questões, 60 min, 65%. Simulados listados no dropdown (sem modo aleatório).
- Questões por nível de conhecimento (K1–K4) com destaque visual.
- Suporte a questão de única escolha (radio) e múltipla escolha (checkbox).
- **Tela de resultado:** para cada questão, exibe sua resposta, a correta e, quando houver, a **explicação** (“Por quê?”) da resposta correta.
- Histórico de tentativas **separado** por tipo de exame (CTFL e CTFL-AT), salvo no navegador (LocalStorage).
- Timer regressivo, gabarito detalhado, exportação de gabarito (PDF) e histórico das últimas tentativas.

## 🚀 Como Usar

1. **Suba um servidor local** (o carregamento dos JSON dos simulados não funciona abrindo `index.html` direto pelo disco):
   ```bash
   npx serve
   ```
   Ou, com npm:
   ```bash
   npm start
   ```
   Acesse o endereço exibido (ex.: `http://localhost:3000`).

2. Escolha o **tipo de exame** (CTFL ou CTFL-AT) e o **simulado** na lista.

3. Clique em **Iniciar Quiz**, responda às 40 questões e use **Finalizar Quiz** ao terminar (ou ao esgotar o tempo).

4. Na tela de resultado, confira acertos/erros e as **explicações** (“Por quê?”) quando disponíveis.

5. Use **Histórico de Tentativas** e **Ver Gabarito** para revisar tentativas anteriores.

> **Dica:** Se aparecer "Failed to fetch", você está abrindo por `file://`. Use sempre `npx serve` (ou outro servidor local) na pasta do projeto.

## Estrutura das Questões (JSON)

Cada questão pode ter:

- **Obrigatórios:** `id`, `questao`, `alternativas`, `correta`, `tipo`, `level`, `imagens`
- **Opcional:** `explicacao` ou `justificativa` — texto exibido na correção como “Por quê?” (motivo da resposta correta)

**Exemplo:**

```json
{
  "questoes": [
    {
      "id": "01",
      "questao": "Enunciado da questão.",
      "alternativas": {
        "A": "Texto da alternativa A",
        "B": "Texto da alternativa B",
        "C": "Texto da alternativa C",
        "D": "Texto da alternativa D"
      },
      "correta": "B",
      "tipo": "Radio button",
      "imagens": [],
      "level": "K1",
      "explicacao": "Justificativa opcional: por que B é a resposta correta."
    }
  ]
}
```

- **Múltipla escolha:** use `"tipo": "Checkbox"` e `"correta": ["A", "C"]`.
- **Explicação:** o simulador procura, nesta ordem: `explicacao`, `justificativa`, `comentario`, `explanation`. Se existir e não estiver vazio, será mostrado na tela de resultado.

## Critérios de Aprovação

- **Nota mínima:** 65% (26 de 40 pontos).
- **Tempo:** 60 minutos por tentativa.
- **Questões:** 40 por simulado.

## Tecnologias

- HTML5, CSS3 (Tailwind CSS), JavaScript
- LocalStorage para histórico por tipo de exame (CTFL e CTFL-AT)
- Servidor estático recomendado: `serve` (via `npx serve` ou `npm start`)

## Estrutura do Projeto

```
simulador-ctfl/
├── index.html
├── package.json          # scripts: npm start / npx serve
├── scripts/
│   └── functions.js
├── styles/
│   ├── globals.css
│   ├── desktop.css
│   └── mobile.css
├── Simulados/
│   ├── SimuladoA (Oficial BSTQB).json
│   ├── SimuladoB (Oficial BSTQB).json
│   ├── SimuladoC (Oficial BSTQB).json
│   ├── SimualdoD (Não oficial Gerado por IA).json
│   └── CTFL-AT/
│       └── SimuladoA.json   # 40 questões + justificativas
└── README.md
```

Novos simulados CTFL-AT podem ser colocados em `Simulados/CTFL-AT/` e referenciados em `scripts/functions.js` na lista `simuladosArquivosCTFLAT`. Também é possível **Importar JSON** pela interface para carregar um arquivo de questões sem alterar o código.

---

// Este código é baseado no projeto original de Matteus Bonotto: https://github.com/matteusbonotto/simulador-ctfl

// Modificado por: Jefferson Farias

Simulador CTFL e CTFL-AT para estudos das certificações ISTQB Foundation Level e Agile Tester.
