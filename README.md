# emb22109-rtos-scheduling
Resolução da lista de exercícios de escalonamento em tempo real da cadeira de Sistemas Embarcados. A resolução é feita
no próprio arquivo [respostas.tex](respostas.tex) por meio do
[SageTeX](https://doc.sagemath.org/html/pt/tutorial/sagetex.html). Para compilar o arquivo .tex, incluindo o
processamento feito pelo [SageMath](https://www.sagemath.org/), deve ser compilado uma primeira vez com o seu compilador favorito, processado com o SageMath, e compilado novamente, agora com os resultados do SageMath.

## Configuração do ambiente
A compilação do documento .tex foi realizada em uma máquina com sistema operacional Windows 10 build 19043.1620.

As bibliotecas Python usadas foram instaladas dentro do ambiente Cygwin proveniente da instalação do SageMath. As
seguintes bibliotecas foram instaladas com o gerenciador de pacotes `pip` utilizando o SageMath Shell:
```Python
pip install parse plotly pandas CairoSVG
```

Foi utilizado o programa [MiKTeX](https://miktex.org/) para a instalação e gerenciamento dos pacotes TeX e o *front-end* gráfico
[TeXworks](https://www.tug.org/texworks/) para escrever o documento. Para a compilação automática o TeXworks pode ser configurado como na imagem abaixo:

![Imagem da configuração do TeXworks para compilação automática](imagens/texworks.png "Compilação automática com
        TeXworks")

Nessa imagem foi adicionada a compilação com as ferramentas LuaLaTeX+SageTeX+MakeIndex+BibTeX, o seu comando a ser apontado é o `bash.exe` do ambiente Cygwin embutido no SageMath, localizado no diretório `%LocalAppData%\SageMath 9.3\runtime\bin` (**somente diretórios absolutos são aceitos na configuração do TeXworks**). Após o comando ter sido selecionado os seguintes argumentos são passados à ele (**argumentos com \%LocalAppData\% devem ser substituídos pelo caminho AppData\Local da máquina em questão atentando pela utilização de barras para caminhos de comando com Linux e contrabarras para caminhos do Windows**):
```
--login
'/opt/sagemath-9.3/sage'
-sh
-c
cd "$OLDPWD" && rm -f $basename.sagetex.* && "%LocalAppData%/Programs/MiKTeX/miktex/bin/x64/miktex-luahbtex.exe" $synctexoption --fmt=lualatex $fullname && sage $basename.sagetex.sage && "%LocalAppData%/Programs/MiKTeX/miktex/bin/x64/texify.exe" --pdf --engine=luahbtex --synctex=1 --clean $fullname && exit
```
Recomenda-se que o navegador tenha a opção de *download* automático habilitada para que os arquivos de imagem sejam baixados sem interação humana. 
