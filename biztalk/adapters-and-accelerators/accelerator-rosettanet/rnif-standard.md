---
title: Norme RNIF | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RNIF, message definitions
- RNIF, messaging framework patterns
- messages, message definitions
- RNIF, standards
- messages, messaging framework patterns
ms.assetid: d39a9683-1ef5-462b-9472-4e30fe873f7d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6b29d8c9c770893fd78769b86266ce33e31a336
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="rnif-standard"></a>Norme RNIF
La norme RNIF (RosettaNet Implementation Framework) définit comment les systèmes transportent un message RosettaNet. La norme RNIF est une norme de transfert, de routage, d'empaquetage et de sécurité fiable. Tous les systèmes de messagerie RosettaNet doivent respecter la norme RNIF pour obtenir la certification RosettaNet.  
  
 La norme définit la structure des messages, la nécessité d'accusés de réception, le codage MIME (Multipurpose Internet Mail Extensions) et la signature numérique. La norme principale inclut une configuration requise pour l'authentification, l'autorisation, le chiffrement et la non-répudiation. La norme RNIF est basée sur les normes HTTP, MIME et XML. La norme RNIF ne spécifie pas de plateforme ou d'application d'activation.  
  
 [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]implémente deux versions de la norme RNIF : spécification de RNIF v02.00.01 et la spécification de RNIF v1.1. RNIF, 2.01 a ajouté des fonctionnalités significatives qui vont au delà de celles prises en charge par RNIF 1.1, notamment le chiffrement, les pièces jointes et les transactions synchrones. RNIF 2.0 n'est pas à compatibilité descendante avec RNIF 1.1.  
  
## <a name="messaging-framework-patterns"></a>Modèles d'infrastructure de messagerie  
 Le tableau suivant présente la prise en charge RNIF des modèles d'infrastructure de messagerie et l'échange de messages synchrone. Un message à action unique est un message qui n'implique pas une réponse, alors qu'un message à double action comprend une demande et une réponse.  
  
|Infrastructure|Motif|Synchrone/<br />Asynchrone|  
|---------------|-------------|---------------------------------|  
|RNIF 1.1|Notification|Asynchrone|  
|RNIF 1.1|Transaction|Asynchrone|  
|RNIF 2.0|Double action|Synchrone|  
|RNIF 2.0|Double action|Asynchrone|  
|RNIF 2.0|Action unique|Synchrone|  
|RNIF 2.0|Action unique|Asynchrone|  
  
## <a name="message-definitions"></a>Définitions de message  
 Les normes RNIF 1.1 et RNIF 2.01 définissent le message RosettaNet différemment. Ces différences incluent la façon dont elles gèrent les pièces jointes, l'enveloppe S/MIME (Secure/Multipurpose Internet Mail Extensions), l'en-tête de remise et l'empaquetage MIME. Notamment, RNIF 2.01 inclut les pièces jointes ; RNIF 2.01 ajoute un en-tête de remise, tandis que RNIF 1.1 ne le fait pas.  
  
> [!NOTE]
>  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]ne prend pas en charge la *recommandations techniques pour RNIF 1.1* publié par l’organisation RosettaNet (une pour la prise en charge de la pièce jointe et une pour les réponses synchrones).  
  
 Les systèmes utilisent les parties des messages RNIF 1.1 et RNIF 2.01 à des fins d'identification de la partie, de routage et d'identification au niveau du service. Avant de lire un corps de contenu de service, qui constitue le contenu principal du message, et d'y répondre, chaque partie doit remplir ou interpréter correctement les valeurs d'en-tête.  
  
 L'illustration suivante décrit les définitions de message RNIF 1.1 et RNIF 2.01.  
  
 ![&#60; Aucune modification &#62; ] (../../adapters-and-accelerators/accelerator-rosettanet/media/rn3-rnif-message-definitions.gif "RN3_RNIF_Message_Definitions")  
  
 Dans le message RNIF 1.1, le numéro de version indique la version de RNIF. La longueur du contenu est la longueur du message de service RosettaNet. Le message de service, qui inclut le préambule, l'en-tête de service et le contenu de service, est une entité MIME à parties multiples/associée. La longueur de la signature est la longueur de la signature en octets. Si la signature existe, il s'agit d'une signature PKCS (Public-Key Cryptography Standards) #7 sur le champ de message de service.  
  
 RNIF 2.01 inclut un conteneur indépendant du protocole de transfert qui empaquette ensemble la charge utile d'entreprise, les composants d'en-tête et d'autres éléments que les systèmes échangeront dans le package. Un message d'entreprise RosettaNet (tel que défini pour RNIF 2.01) contient un préambule, un en-tête de remise, un en-tête de service et un contenu de service. Les systèmes doivent valider tous les éléments par rapport au schéma pour le type de document qui le contient, selon les règles de validation de grammaire de la définition de type de document (DTD, Document Type Definition) standard RosettaNet. Le contenu de service peut être un message d'action ou un message de signal. Si le contenu de service est un message d'action, le message peut inclure une ou plusieurs pièces jointes.  
  
 Un message d'entreprise RosettaNet est une entité MIME à parties multiples/associée. Comme indiqué dans l'illustration précédente, les en-têtes et le contenu de service sont empaquetés ensemble à l'aide d'une construction MIME à parties multiples/associée qui est semblable au schéma d'empaquetage RNIF 1.1. Éventuellement, les systèmes peuvent signer numériquement un message d'entreprise RosettaNet. Dans RNIF 1.1, vous utiliseriez le format RNO (RosettaNet Object) à cet effet. RNIF 2.0 supprime le format RNO, et utilise à la place le codage S/MIME standard.  
  
 Un système peut chiffrer la charge utile ou le conteneur de charge utile RNIF 2.01. Pour ce faire, vous regroupez les parties que vous souhaitez chiffrer dans une entité MIME à parties multiples/associée, puis vous les chiffrez. Vous empaquetez ensuite l'objet S/MIME obtenu en tant que partie unique dans le message d'entreprise RosettaNet.  
  
 Un message de signal doit toujours être une instance de message de signal définie par RosettaNet. Pour les messages d'action, la spécification RNIF 2.01 offre la possibilité d'expédier les messages d'action d'entreprise dans un format défini par un tiers. L'en-tête de service RNIF 2.01 inclut des champs supplémentaires à cet effet, par exemple un champ qui identifie le « corps de la norme » et un champ qui identifie la version de la spécification à laquelle le message d'action est conforme.  
  
 Seuls les messages d'action (également appelés « contenu d'entreprise ») peuvent avoir une origine autre que RosettaNet. Les systèmes doivent échanger ces messages dans un PIP défini par RosettaNet. RosettaNet doit sanctionner ces messages en identifiant explicitement le message d'action tiers sanctionné dans la spécification PIP. En outre, les partenaires commerciaux doivent s'entendre dans leur accord de partenariat commercial pour échanger un contenu d'entreprise tiers. L'accord doit inclure les informations de liaison de charge utile du PIP, qui identifient le contenu d'entreprise tiers que vous utiliseriez en remplacement d'un message d'action particulier dans un PIP.  
  
## <a name="see-also"></a>Voir aussi  
 [RosettaNet et CIDX normes de messagerie](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-and-cidx-messaging-standards.md)   
 [PIP de RosettaNet](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-pips.md)