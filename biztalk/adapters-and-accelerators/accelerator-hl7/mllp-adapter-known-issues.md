---
title: "Problèmes connus de l’adaptateur MLLP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MLLP adapters, known issues
- known issues, MLLP adapters
ms.assetid: 66af8fcc-981a-4a77-80b7-84824bfae608
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5cbae1bf4bf04e2ecf4e643ad5107b9e0fd70f70
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mllp-adapter-known-issues"></a>Problèmes connus de l’adaptateur MLLP
Cette section contient des informations utiles qui peuvent vous aider à éviter les erreurs de protocole de couche inférieure minimale (MLLP) l’adaptateur.  
  
## <a name="two-way-mllp-adapter-might-not-detect-a-problem-with-an-ack"></a>L’adaptateur MLLP bidirectionnelle peut ne pas détecte un problème avec un accusé de réception  
 Lorsque [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]) reçoit un accusé de réception (ACK) sur une carte MLLP bidirectionnelle, l’adaptateur effectue une validation léger sur l’accusé de réception pour déterminer sa validité. Si elle n’est pas valide, le champ MSA1 est extrait et en fonction de sa valeur, l’adaptateur effectue une nouvelle tentative, suspend ou supprime le message d’origine auquel l’accusé de réception a été répond. Toutefois, étant donné que la validation effectuée par l’adaptateur n’est pas une validation complète, il est possible que l’adaptateur ne détecte pas un problème avec les accusés de réception. Par exemple, l’adaptateur peut déterminer que l’accusé de réception est valide et supprimer le message d’origine, tandis que le pipeline est déterminer que l’accusé de réception n’était pas correctement formé et suspendre le message d’accusé de réception.  
  
## <a name="mllp-performance-counters-do-not-count-acks"></a>Les compteurs de performance MLLP ne comptent pas les accusés de réception  
 Une mesure de performances est le nombre de messages traités par un adaptateur MLLP, comme indiqué par les compteurs de performance MLLP. Ce compteur mesure le nombre de messages reçus ou transmis. Toutefois, le nombre ne mesure pas le nombre d’accusés de réception reçus ou envoyés.  
  
## <a name="mllp-adapter-connection-names-are-not-guaranteed-to-be-unique"></a>Noms de connexion de l’adaptateur MLLP ne sont pas garantis pour être unique  
 [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)]ne garantit pas l’unicité du nom de connexion entré dans les pages de propriétés d’un adaptateur MLLP. Vérifiez que cette connexion descriptive et applique des noms sont entrés dans ce champ obligatoire. Les noms de connexion qui représentent les applications line-of-business peut s’avérer utile lors de la tentative de comprendre le comportement de la connexion. Par exemple, les compteurs PerfMon utilisent le nom de connexion.  
  
> [!NOTE]
>  BTAHL7 garantit l’unicité des emplacements de réception ou de noms de ports d’envoi.  
  
## <a name="two-way-mllp-adapters-do-not-send-commit-acks-for-all-messages-in-a-batch"></a>Les adaptateurs MLLP bidirectionnelles n’envoient pas de valider les accusés de réception pour tous les messages dans un lot  
 Lorsque vous configurez chaque message dans un lot pour générer un accusé de réception de validation, le système envoie le lot à l’adaptateur de réception un MLLP bidirectionnelle, l’adaptateur envoie uniquement la valider l’accusé de réception correspondant au premier message dans le lot.  
  
> [!NOTE]
>  Il est recommandé d’utiliser un adaptateur MLLP unidirectionnel pour transporter des lots.  
  
## <a name="nak-generated-by-two-way-mllp-adapter"></a>NAK généré par l’adaptateur MLLP bidirectionnelle  
 Lorsqu’un adaptateur MLLP bidirectionnels suspend tous les messages, l’adaptateur MLLP génère un NAK (accusé de réception négatif) et le place dans la base de données MessageBox. Cela peut être un comportement inattendu. Il pouvez vous souhaitez supprimer le NAK à partir de la base de données MessageBox ou mapper vers un autre message.  
  
## <a name="two-way-mllp-adapter-only-supports-the-2x-message-format"></a>L’adaptateur MLLP bidirectionnelle prend uniquement en charge le format du message 2.X  
 L’adaptateur MLLP bidirectionnelle prend actuellement en charge uniquement le format du message 2.X.  
  
## <a name="two-way-mllp-adapter-does-not-support-static-acknowledgments"></a>Adaptateur MLLP bidirectionnelle ne prend pas en charge les accusés de réception statiques  
 Envoi bidirectionnel adaptateur ne prend pas en charge le traitement des accusés de réception statiques.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes connus](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)