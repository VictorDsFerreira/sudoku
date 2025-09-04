## Sudoku UI (Java)

Um projeto simples de Sudoku em Java com duas formas de execução:
- Console (menu interativo)
- Interface gráfica Swing

### Requisitos
- Java 17+ (JDK)
- Qualquer IDE Java (IntelliJ IDEA recomendado) ou terminal com `javac/java`

### Estrutura principal
- `br/com/dio/Main.java`: versão console do jogo
- `br/com/dio/UIMain.java`: versão com interface gráfica

### Como executar (IDE)
1) Abra o projeto na IDE.
2) Localize a classe `br.com.dio.Main` e rode como aplicação Java para a versão console.
3) Localize a classe `br.com.dio.UIMain` e rode como aplicação Java para a versão UI.

Observação: A versão console agora possui uma configuração padrão embutida do tabuleiro (seed). Assim, você pode rodar sem argumentos que o jogo inicia com um layout válido automaticamente.

### Como executar (terminal)
Compile:
```bash
javac -d out $(git ls-files "**/*.java")
```

Rode a versão console (usa a configuração padrão embutida):
```bash
java -cp out br.com.dio.Main
```

Rode a versão UI (Swing), também sem argumentos:
```bash
java -cp out br.com.dio.UIMain
```

### Passando configurações personalizadas do tabuleiro (opcional)
A aplicação aceita 81 argumentos (um por posição):

Formato de cada argumento: `coluna,linha;valor,fixed`
- `coluna` e `linha`: de 0 a 8
- `valor`: número esperado de 1 a 9
- `fixed`: `true` se o valor é fixo (pré-preenchido), `false` caso contrário

Exemplo (apenas 3 posições mostradas; complete todas as 81 para usar este modo):
```bash
java -cp out br.com.dio.Main 0,0;4,false 1,0;7,false 2,0;9,true ... 8,8;9,false
```

Se algum argumento não for informado, a versão console usará a configuração padrão embutida.

### Menu da versão console
Ao iniciar `Main`, você verá:
- 1: Iniciar um novo Jogo
- 2: Colocar um novo número
- 3: Remover um número
- 4: Visualizar jogo atual
- 5: Verificar status do jogo
- 6: Limpar jogo
- 7: Finalizar jogo
- 8: Sair

Notas:
- Ao inserir/remover número, primeiro informe coluna (0–8), depois linha (0–8), e então o valor (1–9).
- Posições marcadas como fixas (`fixed=true`) não podem ser alteradas.
- O status pode ser: Não iniciado, Incompleto ou Completo. O jogo termina quando está Completo e sem erros.

### Interface gráfica (UI)
- `UIMain` abre a janela principal. Os setores do Sudoku são renderizados via componentes Swing em `br/com/dio/ui/custom`.
- Também funciona sem argumentos, usando a configuração padrão.

### Desenvolvimento
- Classes de domínio: `br.com.dio.model.*` (`Board`, `Space`, `GameStatusEnum`).
- Lógica de exibição do board no console: template em `br.com.dio.util.BoardTemplate`.

### Licença
Uso livre para estudo e experimentos.


