# ExtractorTFIDF

O `ExtractorTFIDF` é uma classe Python desenvolvida pelo Dr. Dheiver Francisco Santos, que permite extrair características TF-IDF (Term Frequency-Inverse Document Frequency) de um conjunto de frases, agrupadas por tipos específicos, e calcular a frequência das palavras importantes em cada tipo de frase.

## Requisitos

- Python 3.x
- Bibliotecas Python: scikit-learn (`sklearn`), numpy (`np`), pandas (`pd`)

## Instalação

Para usar a classe `ExtractorTFIDF`, certifique-se de ter as bibliotecas necessárias instaladas. Você pode instalá-las via `pip`:

```bash
pip install scikit-learn numpy pandas
```

## Autor

**Dr. Dheiver Francisco Santos**  
Especialista em Processamento de Linguagem Natural (PLN) e Análise de Dados.

- LinkedIn: [Dr. Dheiver Francisco Santos](https://www.linkedin.com/in/dheiver-santos)
- Website: [www.dheiver.com](http://www.dheiver.com)

## Uso

1. **Importar a classe ExtractorTFIDF:**

   ```python
   from ExtractorTFIDF import ExtractorTFIDF
   ```

2. **Definir frases e tipos:**

   ```python
   frases = [
       "O céu está azul hoje.",
       "A primavera chegou mais cedo este ano.",
       "Gosto de caminhar ao pôr do sol.",
       "A vida é uma jornada cheia de surpresas.",
       "A ciência avança a passos largos.",
       "A música é a linguagem universal."
   ]

   tipos = [
       "Meteorologia",
       "Meteorologia",
       "Meteorologia",
       "Filosofia",
       "Filosofia",
       "Filosofia"
   ]
   ```

3. **Criar uma instância de ExtractorTFIDF:**

   ```python
   extractor = ExtractorTFIDF()
   ```

4. **Extrair características TF-IDF:**

   ```python
   df_resultado = extractor.extract_tfidf_features(frases, tipos, min_words=3)
   ```

   - `min_words` é o número mínimo de palavras que uma frase deve ter para ser considerada na análise.

5. **Exibir resultados:**

   ```python
   print("DataFrame com as palavras importantes e suas pontuações TF-IDF:")
   print(df_resultado)
   ```

6. **Contar frequência das palavras importantes:**

   ```python
   df_final = pd.DataFrame()

   for tipo in df_resultado['Tipo'].unique():
       df_tipo = df_resultado[df_resultado['Tipo'] == tipo]
       df_frequencia_palavras = extractor.contar_frequencia_palavras_importantes(df_tipo, tipo)
       df_final = pd.concat([df_final, df_frequencia_palavras], ignore_index=True)

   print("\nDataFrame final com a frequência das palavras importantes para todos os tipos:")
   print(df_final)
   ```

## Funcionamento

- **extract_tfidf_features(sentences, tipos=None, min_words=0):**
  - Extrai características TF-IDF para frases agrupadas por tipos específicos.
  - Calcula as palavras mais importantes, média e desvio padrão das pontuações TF-IDF, e contagem de palavras em cada frase.

- **contar_frequencia_palavras_importantes(df, tipo=None):**
  - Conta a frequência das palavras importantes em um DataFrame de resultado, opcionalmente filtrado por tipo de frase.

## Contribuições

Contribuições são bem-vindas! Sinta-se à vontade para abrir problemas (`issues`) ou enviar `pull requests` para melhorias.
