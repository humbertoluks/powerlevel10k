# Customizar o ZSH com PowerLevel10K

1. **Instalar as fontes MesloLGS NF**
   
   Realizar o download das fontes MesloLGS listadas aqui. São um total de 4 fontes
   
   - [MesloLGS NF Regular.ttf](https://github.com/humbertoluks/powerlevel10k/blob/master/MesloLGS%20NF%20Regular.ttf)
   
   - [MesloLGS NF Italic.ttf](https://github.com/humbertoluks/powerlevel10k/blob/master/MesloLGS%20NF%20Italic.ttf)
   
   - [MesloLGS NF Bold.ttf](https://github.com/humbertoluks/powerlevel10k/blob/master/MesloLGS%20NF%20Bold.ttf)
   
   - [MesloLGS NF Bold Italic.ttf](https://github.com/humbertoluks/powerlevel10k/blob/master/MesloLGS%20NF%20Bold Italic.ttf)  
   
   Instale todas elas

2. **Customizar o perfil do iTerm2  com uma predefinição**
   
   Baixe o perfil que estou usando [aqui](https://github.com/humbertoluks/powerlevel10k/blob/master/powerlevel10k-itermcolors.json) e importe-o para o iTerm2. Para importar a predefinição de perfil, vá para **iTerm2** -> **Preferences** -> **Profile** -> **Other Actions…** -> **Import JSON Profiles**.  
   
   Saia e reinicie o iTerm2  

3. I**nstalar Oh my Zsh e os plugins**
   
   [Oh my Zsh](https://github.com/robbyrussell/oh-my-zsh) é um framework de configuração para Zsh.
   
   ```shell
   sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"`
   ```
   
   Instale o plugin Auto suggestions(for Oh My Zsh)
   
   ```shell
   git clone https://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
   ```
   
   então instale zsh-completions e zsh-syntax-highlighting.
   
   ```shell
   brew install zsh-completions zsh-syntax-highlighting
   ```
   
   Agora é hora de editar seu .zshrc e carregar alguns plugins Oh my Zsh e terminar o plugin zsh-syntax-highlighting.
   
   ```shell
   vi ~/.zshrc
   ```
   
   Procure a seção de plugins e edite conforme abaixo. Você pode encontrar mais e ler o que os plugins fazem [aqui](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins).  
   
   dotenv é particularmente útil, pois você pode criar um arquivo .env com suas variáveis ​​ENV que o plug-in carregará automaticamente quando você estiver dentro do diretório raiz do seu projeto.
   
   ```
   ```textile
   # Example format: plugins=(rails git textmate ruby lighthouse)
   # Add wisely, as too many plugins slow down shell startup.
   plugins=(
       git
       zsh-completions
       macos
       sudo
       dotenv
   )
   ```
   ```
   
   Você também precisa adicionar a seguinte linha para estar no final do arquivo.
   
   ```textfile
   source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
   ```
   
   

4. Baixe meu arquivo p10k.zsh [aqui](https://github.com/humbertoluks/powerlevel10k/blob/master/p10k.zsh). Copie-o para sua pasta pessoal e renomeie-o para .p10k.zsh.  
   
   Adicione as seguintes linhas na parte superior do arquivo .zshrc. Isso é para habilitar o recurso de prompt instantâneo do Powerlevel10k.
   
   ```textfile
   # Enable Powerlevel10k instant prompt. Should stay close to the top of ~/.zshrc.
   # Initialization code that may require console input (password prompts, [y/n]
   # confirmations, etc.) must go above this block; everything else may go below.
   if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
     source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
   fi
   ```
   
   Em seguida, procure a configuração ZSH_THEME e edite-a para usar powerlevel10k.
   
   ```textile
   ZSH_THEME="powerlevel10k/powerlevel10k"
   ```
   
   Todas as personalizações do Powerlevel10K estão localizadas no arquivo [.p10k.zsh](https://github.com/humbertoluks/powerlevel10k/blob/master/p10k.zsh) que você baixou do meu repositório git. Adicione a seguinte linha no final do seu arquivo ~/.zshrc para carregá-lo.  
   
   ```textile
   # To customize prompt, run `p10k configure` or edit ~/.p10k.zsh.
   [[ ! -f ~/.p10k.zsh ]] || source ~/.p10k.zsh
   ```
   
   Recarregue .zshrc e seu terminal zsh agora deve se parecer com a minha configuração.
   
   ```shell
   source ~/.zshrc
   ```
   
     Caso a seguinte mensagem seja exibida para voçê `# zsh compinit: insecure directories and files, run compaudit for list`, siga essa sujestão.
   
   Abra o terminal e digite
   
   ```shell
   compaudit
   ```
   
   Para cada diretório que for exibido faça
   
   ```shell
   sudo chown -R [your user name] target_directory
   sudo chmod -R 755 target_directory
   ```

        Feche e reinicie o terminal.
