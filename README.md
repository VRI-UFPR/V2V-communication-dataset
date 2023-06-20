### PREVIEW DATASET
Ideia inicial de como funcionaria o dataset das simulações de ataque a comunicação V2V.

### ATAQUES
Atualmente, possuo 6 diferente simulações, sendo elas:
    - NO_ATTACK: simulação da comunicação V2V como deveria ser, sem nenhum agente malicioso.
    - EUCLIDIAN_DISTANCE: Calcula a distancia do carro alvo, para o carro do atacante e envia a mensagem como se estivesse a exata mesma distância, porém a sua frente.
    (Só tem sentido se o carro atacante estiver atrás do alvo, caso contrario a localização é a real)
    - SIDE_DISTANCE: O atacante envia mensagem como se estivesse ao lado do alvo.
    (A distância entre faixas foi calculada utilizando diversas simulacoes de troca de faixa)
    - DIAGONAL_DISTANCE: O atacante envia mensagem como se estivesse nas diagonais do alvo.
    (Junção dos ataques acima)
    - ALL_LOCATIONS: O atacante simula como se estivesse em todos os ataques acima ao mesmo tempo.
    - ALL_LOCATIONS_RANDOM: O mesmo ataque anterior, porém as distancias sao aleatorias variando [0, distancia fixa].

### ANATOMIA DO LOG
No primeiro nivel do log estão os log dos simuladores. Mais importante para esse momento seria o log do ns3, simulador da rede, implementando o padrão IEEE 802.11p.

Dentro da pasta apps, estão os logs individuais de cada veiculo.

Os veiculos que possuem o log "AutobotVehicle" representam os veículos que se comunicam da forma adequada. Nos exemplos, eles são representados por veh_0.

Os veiculos que possuem o log "DecepticonVehicle" representam os veículos que podem forjar sua localização. Nos exemplos, eles são representados por veh_1.

### Proximos passos.
    - [] Atualmente, todas as mensagens tem como origem o mesmo nodo, o proximo passo seria mudar a assinatura de origem do nodo na rede, de tal forma que cada localização forjada tenha uma origem diferente.

    - [] As mensagens de localização forjada são enviadas uma em sequencia da outra. O ideal seria que houvesse um espaço de tempo entre cada uma delas de forma a parecer mais natural.