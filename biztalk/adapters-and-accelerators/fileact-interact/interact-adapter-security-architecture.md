---
title: "Interagir l’Architecture de sécurité de carte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4924b8c-1fda-4a0c-b9be-8f2ccba38013
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de0eee57daec102507a9e502e3146e1cfcdec723
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interact-adapter-security-architecture"></a>Interagir l’Architecture de sécurité de carte
Sécurité pour la transmission des messages et la réception est implémentée à l’aide des fonctionnalités de certificat et de chiffrement inhérents aux liens SWIFTNet (SNL) et la passerelle SWIFTAlliance (trous). SWIFT recommande que les services conçus pour interagir appliquer une signature « de bout en bout », autrement dit, pour signer la demande et réponse des messages.  
  
 Les opérations de chiffrement sont implémentées par le module de sécurité de liaison de SWIFTNet. Ce module permet de signature et chiffrement à l’aide de clés de l’infrastructure à clé publique. La nature et l’étendue des opérations de chiffrement sont spécifiés en tant que partie des structures de données de demande et réponse contrôle passé à l’API.  
  
 SWIFTNet prend en charge l’authentification/chiffrer du RequestPayload ou ResponsePayload. Le RequestHeader ou ResponseHeader peut également être signé.  
  
## <a name="signingencrypting-requests-and-responses"></a>La signature et le cryptage des demandes et réponses  
 Les règles pour appliquer des opérations de chiffrement sur SWIFTNet interagir demande les éléments sont les suivantes :  
  
-   RequestControl : il est destiné à SWIFTNet uniquement. SWIFTNet offre un RequestDescriptor le répondeur (et certains éléments également au demandeur). Par conséquent, aucune opération de chiffrement de processus serveur du processus client ne peut être effectué sur celle-ci.  
  
-   RequestE2EControl : cet élément contient des informations pour vous assurer de messagerie fiable de bout en bout. Aucune opération de chiffrement ne peut être effectuée sur celui-ci.  
  
-   RequestHeader : il est utilisé par SWIFTNet et transmis sans modification au répondeur. Par conséquent, il peut uniquement être signé.  
  
-   RequestPayload : toutes les opérations de chiffrement peuvent être effectuées sur ce.  
  
-   Élément (s) chiffrement : ils concernent les opérations de chiffrement précédemment activées sur cette demande. Aucune opération de chiffrement peut être effectuée sur ces.  
  
 Les règles pour l’application des fonctions de chiffrement sur SWIFTNet interagissent les réponses sont :  
  
-   ResponseControl : il est destiné à SWIFTNet uniquement. SWIFTNet offre un ResponseDescriptor au demandeur. Par conséquent, aucun processus de serveur pour l’opération de chiffrement d’un processus client ne peut être effectuée sur celle-ci.  
  
-   ResponseE2EControl : cet élément contient des informations pour vous assurer de messagerie fiable de bout en bout. Aucune opération de chiffrement ne peut être effectuée sur celui-ci.  
  
-   ResponseHeader : cet élément peut être signé (il est transféré inchangée au demandeur).  
  
-   ResponsePayload : peuvent être chiffrés et/ou signés.  
  
-   Élément (s) chiffrement : ils concernent les opérations de chiffrement précédemment activées sur cette demande. Aucune opération de chiffrement peut être effectuée sur ces.  
  
## <a name="receiving-requests-with-cryptography"></a>Recevoir des demandes de chiffrement  
 Un processus serveur peut recevoir les requêtes qui ont été soumis à des opérations de chiffrement par le demandeur. La demande entrante contient toutes les informations pertinentes pour activer les opérations de chiffrement inverses. Les informations CryptoInternal sont telle que la fonction de vérification et de déchiffrement efficacement fonctionne à présent.  
  
 Le processus serveur doit activer les contextes de sécurité des noms uniques pour les besoins de déchiffrement s’effectuent  
  
 La demande sera ensuite modifiée par les opérations de chiffrement inverses (vérifier, déchiffrer) de sorte que la demande d’origine sera accessible en l’état au processus serveur, il a été initialement fourni par le processus de client pour le chiffrement opérations. Pour la réponse, le traitement similaire a lieu. Il est important de savoir que la vérification de signature uniquement ne vérifiera pas ce qui a été signé n’a pas modifié, mais qu’il doit authentifier si le signataire est authentique. Cela nécessite que le SignDN utilise un certificat valide. Un certificat valide est un certificat n’a pas été révoqué (il s’agit d’une recherche dans la liste de révocation de certificats, conservées de manière centralisée dans SWIFTNet).  
  
## <a name="activation"></a>Activation  
 SWIFTNet lien peuvent fonctionner de vérification et déchiffrement en mode automatique pour toutes les demandes entrantes et entrant les réponses. Cela signifie que SWIFTNet lien traitera automatiquement (vérifier et déchiffrer) le chiffrement du dernier bloc de toutes les télécopies entrantes (côté serveur) de demandes ou réponses entrantes (côté client). Les conditions requises sont que le contexte de sécurité requis pour le déchiffrement (si le déchiffrement est demandé) est ouvert et que le lien de SWIFTNet a été initialisé en mode automatique (ce paramètre pour le mode automatique est effectué sur le Sw:InitRequest ou Sw:HandleInitResponse, par définition de la CryptoMode sur « Automatique » ou mieux encore « Advanced » pour interagir. (Nous allons utiliser toujours « Avancé » pour l’adaptateur interagir, car cela permet à l’application cliente ou serveur récupérer le formulaire inattendue de chiffrement par la partie distante, ou à partir d’un certificat arrivé à expiration.  
  
 SWIFTNet lien opère la signature et chiffrement automatiquement sur une demande sortante (ou une réponse sortante) si le champ RequestCrypto (ResponseCrypto) est initialisé à « TRUE » dans la RequestControl (ResponseControl) de la demande (réponse).  
  
 Dans ce cas SWIFTNet lien traite le dernier bloc de chiffrement. Les conditions requises sont que le contexte de sécurité requis pour la signature (si la signature est demandé) est ouvert, que le bloc de chiffrement est présent dans la demande avec une indication sur la signature et de chiffrement requis et que le RequestCrypto (ResponseCrypto) indicateur est défini sur « TRUE » dans la RequestControl (ResponseControl). Cela s’effectue toujours, quel que soit le CryptoMode utilisé lors de l’initialisation du client ou du serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Interagir l’Architecture de l’adaptateur](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md)   
 [Composants d’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md)   
 [Interaction des Messages de la carte pour l’échange](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md)   
 [Application cliente de l’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md)   
 [Application de serveur de l’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md)   
 [Interagir de magasin de l’adaptateur et le transfert](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md)   
 [Interagir remise fiable de bout en bout pour l’adaptateur](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md)   
 [Interagir l’état de la carte d’analyse](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md)   
 [Interagir carte de non-répudiation](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)