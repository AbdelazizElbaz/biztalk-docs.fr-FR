---
title: "L’encodeur d’ESB JMS et les composants décodeur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e5591c2-d2ca-4168-8026-059fe51dd588
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f39f4ab1b0650a8ad6fa1ff35d62b4807995237
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-esb-jms-encoder-and-decoder-components"></a>L’encodeur d’ESB JMS et les composants décodeur
Certaines solutions d’intégration impliquent Service JMS (Java Message) et les messages SOAP envoyés vers ou à partir d’IBM WebSphere MQ ; [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] comprend deux composants de pipeline JMS écrits en code managé pour une utilisation dans ces situations. Les composants de lire ou écrire la partie JMS de l’en-tête de message MQ en utilisant les valeurs des propriétés de contexte associées au message. Actuellement, il n’y a plus de 60 différents types d’en-têtes JMS en cours d’utilisation avec les systèmes de WebSphere MQ Series ; les composants ESB JMS fonctionnent uniquement avec les en-têtes de MQRFH2.  
  
## <a name="installation"></a>Installation  
 L’installation du noyau ESB installe automatiquement les composants JMS encodeur et décodeur de JMS dans le dossier composants de Pipeline BizTalk Server.  
  
## <a name="how-it-works"></a>Fonctionnement  
 Les composants de pipeline JMS inspecter les en-têtes de message et fonctionne uniquement sur les messages qui ont le **MQMD_Format** en-tête défini sur **RFH (MQRFH2)**. Toutefois, même si cette propriété est définie, les composants d’inspecter les en-têtes pour confirmer qu’ils ne sont pas conformes au format RFH2 d’IBM. Si l’en-tête n’est pas conforme à ce format, les composants de génèrent une erreur d’analyse qui indique le **MQMD_Format** paramètre a la valeur **RFH (MQRFH2)**, mais la structure de l’en-tête n’a pas respecté la norme RFH2. Si l’analyse de l’en-tête de message entrant échoue, le composant décodeur permet de transmettre le message, mais il définit une propriété de contexte de message nommée **MQRFH2_ParseError** à **True**.  
  
 Le **MQRFH2** schéma de propriété déployé dans BizTalk avec les composants JMS expose toutes les propriétés d’en-tête MQRFH2. Après la rétrogradation les en-têtes d’un message entrant, se trouvent les données à partir des en-têtes dans un document XML stocké dans le **MQRFH2_NameValueData** propriété de contexte du message. L’encodeur ajuste la longueur de la **NameValueData** dossier pour s’assurer qu’elle est la longueur correcte. Pour comprendre l’utilisation de ces en-têtes et l’impact lorsque vous modifiez les valeurs, consultez la documentation IBM appropriée.  
  
## <a name="using-the-jms-encoder-and-decoder-components"></a>À l’aide de l’encodeur JMS et les composants décodeur  
 Pour utiliser les composants JMS encodeur et décodeur, les développeurs les ajoutent à des pipelines dans une application BizTalk. Pour un pipeline d’envoi, le composant encodeur de JMS doit résider dans la phase de codage. Pour un pipeline de réception, le composant décodeur de JMS doit résider dans la phase de décodage. Les composants JMS n’installera pas dans toutes les étapes d’un pipeline.  
  
 Lors de l’installation dans la phase de codage, le composant de JMS encodeur lit les valeurs dans le JMS **MQRFH2** les en-têtes et les écritures (promeut) dans les propriétés de contexte de message. Lors de l’installation dans la phase de décodage, le composant décodeur de JMS lit (rétrograde) valeurs de la propriété de contexte et les insère dans le JMS **MQRFH2** en-têtes. Cela signifie que toutes les valeurs d’en-tête MQ sont disponibles en tant que propriétés de contexte du message dans le pipeline.  
  
 Pour détecter et gérer les erreurs de l’analyse des en-têtes, les développeurs peuvent inclure du code qui examine la valeur de la **MQRFH2_ParseError** propriété. Elles peuvent implémenter un processus de récupération qui s’abonne aux messages ayant échoué ou spécifier des ports d’envoi qui filtre le **MQRFH2_ParseError** propriété pour conserver le message. Les abonnés qui fonctionnent avec les messages JMS doivent inclure une condition de filtre qui spécifie la valeur **False** pour le **MQRFH2_ParseError** propriété pour empêcher l’abonné à partir de la réception des messages Échec de l’en-tête de l’analyse de processus.  
  
 Les développeurs peuvent également mettre à jour les valeurs de propriété de contexte (par exemple, remplacez le **MQRFH2_Encoding** valeur de la propriété), et le composant reflète ces modifications dans les en-têtes de message MQ afin qu’ils sont définis lorsque le message arrive à sa destination finale. Le composant automatiquement ignore les valeurs non valides et définit les valeurs par défaut « sécurisée » où les en-têtes requis sont manquants. Par exemple, si le développeur spécifie une valeur non valide pour le **MQRFH2_Encoding** propriété, le message sortant a la **MQRFH2_Encoding** en-tête défini sur **inconnu**. Si le développeur supprime une valeur d’une propriété de contexte, mais la **MQMD_Format** est toujours définie sur **RFH**, le composant ajoutera un en-tête qui contient la valeur par défaut, conformément à la spécification d’IBM.  
  
 Pour obtenir un exemple d’utilisation de ces composants, consultez [installer et exécuter l’exemple de composant JMS MQRFH2](../esb-toolkit/installing-and-running-the-jms-mqrfh2-component-sample.md).