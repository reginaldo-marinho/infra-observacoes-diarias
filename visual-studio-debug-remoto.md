# Debug Remoto  
Para fazer o debug remoto é necessário que haja dois computadores no contexto. Podemos chama-los de Cliente e Servidor

![image](https://github.com/user-attachments/assets/7aee995f-fbce-4946-bf82-6a4067be0c6c)

## Servidor

- No servidor, você deverá instalar o Visual Studio, pois é neste ponto que as Ferramentas para suporte Remoto serão instaladas
- [Aqui](https://learn.microsoft.com/en-us/visualstudio/debugger/remote-debugging-aspnet-on-a-remote-iis-computer?view=vs-2022#BKMK_setup) é dito para pesquisar na barra de pesquisar por **Remote Debugger**, mas para mim não funcionou, então prefira ir diretamente no local do arquivo `C:\Program Files\Microsoft Visual Studio\2022\Community\Common7\IDE\Remote Debugger\x64\msvsmon.exe`
- > Lembre-se de executar como Adminstrador
  ![image](https://github.com/user-attachments/assets/7a99c58a-1627-4b58-9923-32584607e37e)


## Cliente
- Abra o Visual Studio como Administrador
- Va em Debug
  - Attach to Process
    
![image](https://github.com/user-attachments/assets/aeabfaa9-f7f2-42ac-a6b1-59c1f347738c)
- Em Attach to Process
    - Clique em Find
    - Selecione o `Servidor` presente em Auto Detected

![image](https://github.com/user-attachments/assets/77ae54da-d996-4c62-8959-30d92e1a77bb)

Agora e seguir com o Debug 👍



