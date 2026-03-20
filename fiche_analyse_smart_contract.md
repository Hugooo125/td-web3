Phase 1 — Observation de l’interface

Oui, les résultats du vote s’affichent avant la connexion à MetaMask. Cela est possible car la blockchain est publique et transparente. Les données comme le nombre de votes sont accessibles à tous sans authentification, car elles sont stockées directement sur le réseau Ethereum.

On retrouve dans l’interface l’adresse du contrat, un lien vers Etherscan, le nombre de votes par candidat, un historique des transactions ainsi qu’une explication du fonctionnement de l’application.

Phase 1.2 — Connexion MetaMask

Après la connexion à MetaMask, l’adresse du wallet de l’utilisateur s’affiche et il devient possible de voter. MetaMask ne demande pas de login ni de mot de passe. Cela montre que dans le Web3, l’authentification repose sur le wallet et la clé privée, contrairement au Web2 où l’on utilise un compte avec identifiant et mot de passe.

Phase 2 — Vote et transaction

Lors du vote, MetaMask affiche l’adresse du contrat avec lequel on interagit. Une estimation des frais de gas est également affichée. Le vote coûte du gas car il modifie l’état de la blockchain. Toute écriture sur la blockchain nécessite du calcul, exécuté par l’EVM, ce qui justifie le coût.

Une fois la transaction confirmée, elle est incluse dans un bloc. Le gasUsed correspond à la quantité réelle de calcul utilisée. Il est inférieur au gasLimit car ce dernier représente la limite maximale que l’on accepte de payer, alors que le gasUsed est la consommation réelle.

Phase 2.3 — Cooldown

Lorsque l’on essaie de voter une deuxième fois immédiatement, un message indique qu’il faut attendre. Cette restriction est gérée par le smart contract et non par le frontend, car même en changeant d’interface, la règle s’applique toujours. Elle repose sur une variable qui enregistre le dernier vote et une fonction qui calcule le temps restant avant le prochain vote.

Phase 3 — Analyse sur Etherscan

La première transaction du contrat correspond à son déploiement. Elle est différente des autres car elle initialise le contrat, alors que les suivantes appellent des fonctions comme vote.

Un event nommé "Voted" est émis à chaque vote. Il contient l’adresse du votant et l’index du candidat. Les events servent à notifier et à suivre les actions sur la blockchain sans modifier directement les données stockées. Une variable stocke une information, alors qu’un event sert à signaler une action.

La condition require dans la fonction vote permet de vérifier des règles comme le cooldown. Si la condition n’est pas respectée, la transaction est annulée.

Le parentHash d’un bloc correspond au hash du bloc précédent. Il est essentiel car il lie les blocs entre eux. Si un bloc est modifié, cela casse toute la chaîne, ce qui garantit l’immuabilité de la blockchain.

Phase 4 — Analyse critique

L’immuabilité est utilisée car les votes ne peuvent pas être modifiés. La transparence est exploitée car tout le monde peut vérifier les résultats. La désintermédiation est présente car il n’y a pas de serveur central. La décentralisation est également utilisée car le système repose sur un réseau distribué.

Le vote n’est pas totalement anonyme car les adresses sont visibles publiquement. Un utilisateur peut contourner le cooldown en utilisant plusieurs wallets. Il est aussi possible de créer une autre interface connectée au même contrat, ce qui montre que le contrôle ne dépend pas d’un seul site mais du contrat lui-même.

Verdict final

Cette application est bien conçue car elle utilise la blockchain pour garantir la transparence et l’intégrité des votes. Le système de cooldown est sécurisé car il est géré directement dans le smart contract. Cependant, le vote n’est pas réellement anonyme et peut être contourné avec plusieurs wallets. L’utilisation de la blockchain est pertinente ici car elle empêche toute modification des résultats.

Nom(s) : Floret Hugo

Adresse wallet utilisée pendant l'analyse : 0x1254fBD59EfED833eB8B1C72E840511ABA30E3f5

Hash de votre transaction de vote : 0x0d4f0fefd946ad709be7bacd531658aab2c2dab51026456c3ca90ad682efff37

Numéro du bloc dans lequel votre vote a été inclus : 10483908

En une phrase : qu'est-ce qu'un smart contract, après avoir interagi avec celui-ci ?
Un smart contract est un programme autonome sur la blockchain qui applique des règles automatiquement sans avoir besoin d’un intermédiaire.

En une phrase : quelle est la différence entre ce que fait le frontend (Vercel) et ce que fait le smart contract (Sepolia) ?
Le frontend sert à afficher l’interface et envoyer les actions de l’utilisateur, tandis que le smart contract exécute les règles et enregistre les données sur la blockchain.

La question que cette analyse vous a donné envie de poser :
Est-il possible d'anonymiser ce système de vote?
