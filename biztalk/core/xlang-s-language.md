---
title: Langage XLANG-s | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, properties
ms.assetid: 97b62f17-5a8d-4d87-8563-1f6d941f027f
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2329d4bc42617d70227481a0d70064d368f3c0e7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xlang-s-language"></a>Langage XLANG-s
XLANG/s a été conçu pour utiliser des normes Internet telles que XML, XSD et WSDL (Web Services Description Language), et dispose d'une prise en charge intégrée permettant d'utiliser des messages et objets NET. XLANG/s peut être considéré comme un langage de messagerie comportant certaines des fonctionnalités d'expression de C#. Toutefois, le code n'est pas portable entre XLANG/s et C#.  
  
 XLANG/s favorise une séparation claire entre le processus et l'implémentation. Par exemple, le protocole ou processus d'entreprise est spécifié dans XLANG/s, et les aspects locaux de l'application, tels que l'accès aux bases de données, sont implémentés dans d'autres langages de programmation .NET tels que C# ou Visual Basic.NET.  
  
 La syntaxe d'expression ou d'assignation XLANG/s est modélisée après C#, et vous devez référencer la spécification C# pour obtenir la syntaxe exacte. XLANG/s définit un ensemble complet de constructions de haut niveau permettant de définir des processus d'entreprise. Tandis que XLANG/s prend en charge pour les types de données de bas niveau comme chaîne et entier, les types de données de haut niveau sont également définies : messages, ports, corrélations et liens de service. Ces données servent à permettent de définir la sémantique associée à un processus d’entreprise types et sont complétés par des processus tels que des instructions de contrôle **pendant** ou **étendue**.  
  
 Instructions XLANG/s se décomposent généralement en deux catégories : les instructions simples qui agissent sur leurs propres, telles que **réception** ou **envoyer**et des instructions complexes qui contiennent ou regroupent les deux instructions simples ou autres instructions complexes, tels que **étendue**, **parallèles**, et **écouter**. Les sémantiques représentées dans XLANG/s sont une réflexion de celles définies dans la spécification BPEL4WS (Business Process Execution Language for Web Services) publiée par Microsoft, IBM et BEA pour la définition de la sémantique des processus d'entreprise.  
  
 La maîtrise des principales constructions de XLANG/s est facultative car elles sont créées par les diagrammes d'orchestration de dessin dans le Concepteur d'orchestration BizTalk. Le Concepteur d'orchestration est un outil graphique complet permettant de concevoir visuellement des processus d'entreprise. Il génère des fichiers XLANG/s qui ont une extension .odx et contiennent des informations visuelles supplémentaires dans leurs en-têtes, ainsi que des informations sur les attributs personnalisés dans leurs corps.  
  
> [!NOTE]
>  Le langage XLANG/s est propriétaire et n'est pas entièrement documenté. Cette section présente certaines parties de celui-ci pouvant s'avérer nécessaire lorsque vous développez vos orchestrations. La modification directe des fichiers .odx n'est pas prise en charge.  
  
## <a name="xlangs-programs"></a>Programmes XLANG/s  
 Le programme XLANG/s le plus simple exige qu'un type de message soit défini afin de fournir à l'orchestration les données nécessaires pour démarrer. L'orchestration reçoit le message sur un port puis se termine. Le code suivant en est un exemple :  
  
```  
module HelloWorldApp  
{  
     private porttype ptPOReceive  
     {  
      oneway opPOReceive  
      {  
       HelloWorldApp.PurchaseOrder  
      }  
     }  
     private porttype ptPOSend  
     {  
      oneway opPOSend  
      {  
       HelloWorldApp.PurchaseOrder  
      }  
     }  
     private service  HelloWorld  
     {  
      port implements HelloWorldApp.ptPOReceive poPOReceive;  
      port uses HelloWorldApp.ptPOSend poPOSend;  
      message HelloWorldApp.PurchaseOrder msgPO;  
      body ()  
      {  
       activate receive (poPOReceive.opPOReceive, msgPO);  
       send (poPOSend.opPOSend, msgPO);  
       }  
     }  
}  
```  
  
 Dans le programme XLANG/s précédent, le mot clé `module` définit l'unité de compilation d'un programme XLANG/s. Tous les types utilisés dans le programme, tel que **porttype**, **correlationsettype**, **servicelinktype**, et **messagetype**— sont limités à Ce niveau.  
  
 Un port est une construction qui XLANG/s peut envoyer ou recevoir des messages à partir d’ou et le port a un type défini appelé **porttype**. Le **porttype** construction définit une collection d’opérations qui peuvent être utilisées sur le port. Ces opérations définissent un échange de message valide unique sur le port. Dans la définition **porttype**, **messagetype**, **servicelinktype**, ou **correlationsettype** construit, l’auteur de XLANG/s programme consiste essentiellement à créer les définitions de type de données complexes. Ces définitions présentent les mêmes avantages comme types de données complexes dans d’autres langages : ils extraient les notions représentées dans le type de données à un niveau supérieur, et permettent de réutiliser facilement le type de données.  
  
 Le **ptPOReceive** opération de port de réception port helloworldapp précédent module est défini avec un unidirectionnel **opPOReceive**. Le bloc HelloWorld de service définit l'implémentation réelle du processus et les variables utilisables, dont celles de port et de message. Les trois premières lignes de code dans ce bloc définissent les variables de port **poPOReceive** et **poPOSend** et le message **msgPO** respectivement. Le corps contient le code décrivant les paramètres du service et du comportement d'exécution. Toutes les variables, à l'exception de celles définies avec un bloc d'étendues imbriquées, sont étendues à ce niveau. L’instruction receive, qui est une réception avec activation, reçoit la **msgPO** message à partir de la **poPOReceive.opPOReceive** de port et crée une nouvelle instance de l’orchestration. Une fois le message reçu, l'instruction d'envoi dirige le message vers un port d'envoi. Dans les deux déclarations de port dans le code précédent, **poPOReceive** utilise le modificateur d’implémentation, tandis que **poPOSend** utilise le modificateur d’utilisation. Le modificateur d'implémentation indique au runtime qu'il recevra un message sur ce port. Le modificateur d'utilisation indique au runtime qu'il enverra un message sur ce port.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Types de données XLANG-s](../core/xlang-s-data-types.md)  
  
-   [Instructions XLANG-s](../core/xlang-s-statements.md)  
  
-   [Opérateurs et Variables XLANG-s](../core/xlang-s-variables-and-operators.md)  
  
-   [Expressions XLANG-s](../core/xlang-s-expressions.md)  
  
-   [Mots réservés XLANG-s](../core/xlang-s-reserved-words.md)  
  
-   [XLANG-s pour les Conversions de Type BPEL4WS](../core/xlang-s-to-bpel4ws-type-conversions.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Sur le moteur d’Orchestration BizTalk](../core/about-the-biztalk-orchestration-engine.md)