# Roll ADA — Roll Advanced Dice Arena

Mesa de RPG online em um único arquivo (`index.html`): rolagem de dados, grid de combate, chat, fichas e imagens. Funciona direto no GitHub Pages, sem servidor próprio.

## Como as salas funcionam

- **Criar sala:** o Mestre escolhe um nome e, se quiser, uma senha. A sala existe enquanto a aba do Mestre estiver aberta.
- **Entrar:** o jogador escolhe a sala na lista "Salas abertas" ou digita o nome dela. Se a sala tiver senha, digita a senha.
- **Link de convite:** o botão "Copiar" no topo copia um link (`...?sala=Nome`) que já preenche o nome da sala. A senha você passa à parte.
- A lista de salas é pública e mostra só: nome, se tem senha e quantas pessoas estão dentro. **A senha nunca é publicada.**
- A senha é conferida pelo Mestre antes de qualquer dado da mesa ser enviado. Serve para controlar quem entra entre amigos, não é segurança de banco.

## Para funcionar entre redes diferentes (faça isto uma vez)

Dois jogadores em redes/operadoras diferentes só se conectam de forma confiável com um servidor TURN. O TURN público sem cadastro que vem como reserva não é garantido.

1. Crie uma conta gratuita em https://www.metered.ca/tools/openrelay/
2. No painel, copie o **Domain** (ex.: `seu-nome`) e a **API Key**.
3. Abra `index.html`, procure `TURN_CONFIG` (Ctrl+F) e preencha:

```js
const TURN_CONFIG = {
  meteredAppName: 'seu-nome',
  meteredApiKey: 'SUA_API_KEY'
};
```

4. Suba o arquivo para o GitHub de novo.

## Limites

- Se o Mestre fechar a aba, a sala cai para todos.
- A lista de salas usa brokers MQTT públicos (HiveMQ, EMQX, Mosquitto). Se todos estiverem fora do ar, a lista fica indisponível, mas dá para entrar digitando o nome da sala.
- O encontro entre jogadores usa o serviço público do PeerJS, que não tem garantia de disponibilidade.
- Imagens: até 6 MB (mapa) e 5 MB (chat). Fichas: até 9 MB, até 30 por sala.

## Licenças

Confira a licença dos sprites e dos sons antes de vender. O mqtt.js embutido é MIT; PeerJS e Mammoth são carregados de CDN.
