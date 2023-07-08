### PREVIEW DATASET
Ideia inicial de como funcionaria o dataset das simulações de ataque a comunicação V2V.

Os ataques simulados no dataset sao de forged location e sybil attack, ao mesmo tempo.

### ORGANIZAÇÃO DO ATAQUE

Para a realização do ataque em primeiro momento o atacante cria 2n + 1 nós dummy na rede, onde n é o número de veículos conectados a rede.

O atacante se utiliza desses nós previamente criados para forjar a localização de veículos.

Por meio desses nós é possivel executar o sybil attack, pois os outros veículos vêem a rede com mais nós do que realmente exitem, e além disso o há também o ataque de forge location, pois os nós criados tem localização e movimentação definida pelo atacante.

### TIPOS DE ATAQUE SIMULADOS
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

Os outro veiculos no log são dummies criados para que o atacante possa usar diferentes nodos da rede para enviar as falsas localizações.
