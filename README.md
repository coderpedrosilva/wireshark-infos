# wireshark-infos

### Wireshark - Configurações

| Seção                                                  | Descrição                                                                                     |
|--------------------------------------------------------|------------------------------------------------------------------------------------------------|
| **Edit → Preferences → Appearance → Columns**       | Configura quais colunas de dados serão exibidas (ex.: IP, porta, protocolo).                   |
| **Clicar com o botão direito em cima do nome das colunas → Columns preferences** | Ajusta as colunas visíveis diretamente na interface para personalização rápida.                 |
| **View → Time Display Format** | Define o formato de exibição do tempo nas capturas (ex: tempo absoluto ou relativo).           |
| **View → Coloring Rules**    | Configura as cores para facilitar a identificação de pacotes específicos na captura.           |
| **Edit → Preferences → Filter Buttons** | Adiciona e organiza botões de filtros para acesso rápido durante as análises.                  |
| **Edit → Preferences → Layout** | Ajusta o layout da janela para uma melhor visualização das informações na captura.             |
| **Statistics → Conversations** | Exibe estatísticas detalhadas das conversas entre diferentes endereços e portas.               |

### Filtros Comuns no Wireshark

| Filtro                     | Comando                    | Descrição                                                                                     |
|----------------------------|----------------------------|------------------------------------------------------------------------------------------------|
| **IPv4 Address**           | `ip.addr==10.0.0.1`       | Filtra por endereço IP específico.                                                            |
| **IPv4 Source**            | `ip.src==10.0.0.1`        | Filtra pacotes com origem em um IP específico.                                                |
| **IPv4 Range (Subnet)**    | `ip.addr==10.0.0.0/24`    | Filtra pacotes dentro de um intervalo de IPs, como uma sub-rede.                              |
| **TCP Port**               | `tcp.port==80`            | Filtra pacotes de uma porta TCP específica.                                                   |
| **TCP SYNs**               | `tcp.flags.syn==1`        | Filtra pacotes com flag SYN, usados para iniciar conexões TCP.                                |
| **UDP Port**               | `udp.port==5060`          | Filtra pacotes de uma porta UDP específica, como SIP na porta 5060.                           |
| **UDP**                    | `udp`                     | Filtra todos os pacotes UDP na captura.                                                       |
| **SIP (Todos os Pacotes)** | `sip`                      | Filtra todos os pacotes relacionados ao protocolo SIP.                                         |
| **SIP Porta UDP**          | `udp.port==5060`           | Filtra pacotes UDP para a porta SIP padrão (5060).                                            |
| **SIP INVITE**             | `sip.Method==INVITE`       | Filtra pacotes SIP com o método INVITE (início de uma chamada).                                |
| **SIP BYE**                | `sip.Method==BYE`          | Filtra pacotes SIP com o método BYE (finalização de uma chamada).                              |
| **SIP 200 OK**             | `sip.Status-Code==200`     | Filtra respostas SIP com o código 200 OK (confirmação de sucesso).                             |
| **SIP Redirect (3xx)**     | `sip.Status-Code>=300 && sip.Status-Code<400` | Filtra pacotes SIP com códigos de redirecionamento (3xx).                      |
| **RTP (Todos os Pacotes)** | `rtp`                      | Filtra todos os pacotes relacionados ao protocolo RTP (áudio/vídeo em tempo real).             |
| **RTP Porta UDP**          | `udp.port==10000`          | Filtra pacotes RTP que utilizam uma porta específica, como 10000.                              |
| **RTP Payload Type**       | `rtp.p_type==0`            | Filtra pacotes RTP com payload do tipo 0 (usado em chamadas de áudio G.711).                   |
| **RTP Marcação de Pacote** | `rtp.marker==1`            | Filtra pacotes RTP que contêm marcações, normalmente no início de uma fala ou frame.           |
| **SDP (Todos os Pacotes)** | `sdp`                      | Filtra pacotes que contêm Protocolo de Descrição de Sessão (SDP) dentro de uma negociação SIP. |
| **SDP Media Audio**        | `sdp.media==audio`         | Filtra pacotes SDP que contêm descrições de áudio.                                             |
| **SDP Media Video**        | `sdp.media==video`         | Filtra pacotes SDP que contêm descrições de vídeo.                                             |
| **UDP Port Range**         | `udp.port>=10000 && udp.port<=20000` | Filtra pacotes UDP dentro de uma faixa de portas específica, comumente usada para RTP. |
| **DNS SRV para SIP**       | `dns.qry.name contains "_sip._udp"` | Filtra consultas DNS SRV que buscam registros de serviço SIP sobre UDP.                     |
| **SIP Call-ID**            | `sip.Call-ID=="unique-id"` | Filtra pacotes SIP com um valor específico de Call-ID, usado para rastrear uma sessão única.  |
| **SIP com Texto Específico** | `sip contains "username"`| Filtra pacotes SIP que contêm um texto específico, como um nome de usuário em uma mensagem.    |
| **SIP Authentication**     | `sip.Authorization`        | Filtra pacotes que contêm cabeçalhos de autorização SIP, usados para autenticação.             |

### Operadores nos Filtros do Wireshark

| Operador       | Símbolo/Comando      | Descrição                                                |
|----------------|----------------------|----------------------------------------------------------|
| **Igualdade**  | `==`                 | Compara igualdade entre campos e valores.                |
| **Negação**    | `!`                  | Exclui resultados específicos no filtro.                 |
| **Ou**         | `\|\|`               | Exibe pacotes que atendem a uma ou outra condição.       |
| **E**          | `&&`                 | Exige que duas condições sejam atendidas simultaneamente.|
| **Maior que**  | `gt`                 | Filtra valores maiores que o especificado.               |
| **Menor que**  | `lt`                 | Filtra valores menores que o especificado.               |

Exemplo de filtro completo: `ip.addr eq 192.168.1.1 && tcp`
