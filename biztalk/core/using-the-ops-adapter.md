---
title: "À l’aide de l’adaptateur Ops | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IOpsAIC interface
- Ops adapters, configuring
- Ops adapters, IOpsAIC interface
- process management solution tutorial, Ops adapters
- Ops adapters, processing
ms.assetid: 331f3614-e00b-4587-b82b-3c7bc394f361
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d93436e727265c4b381cdff72c42b3a677d0a4dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-ops-adapter"></a>À l’aide de l’adaptateur Ops
La solution de gestion des processus d'entreprise utilise l'adaptateur Ops pour gérer les rapports d'erreurs à partir de la nouvelle fonction de création de rapports d'erreurs. La solution inclut un exemple de gestionnaire pour traiter les messages de l'adaptateur, bien que vous puissiez facilement écrire le vôtre et utiliser l'adaptateur dans les autres solutions. Pour plus d’informations sur la fonctionnalité de création de rapports d’erreurs, consultez [à l’aide d’Échec de routage des messages](../core/using-failed-message-routing.md).  
  
> [!NOTE]
>  Bien que la solution utilise l'adaptateur pour la création de rapports d'erreurs, son utilisation n'est pas limitée à la gestion des erreurs. Vous pouvez utiliser l'adaptateur dans diverses circonstances lorsque vous voulez exécuter une méthode d'objet spécifique en réponse à un message.  
  
## <a name="how-the-ops-adapter-processes-error-reports"></a>Traitement des rapports d'erreurs par l'adaptateur Ops  
 Dans la solution, les ports qui utilisent le rapport d’erreurs envoient les messages d’erreur pour le **BizTalkErrors-SP** port. Le filtre sur le port vérifie l’existence de la **ErrorReport.ErrorType** propriété de contexte. Seuls les messages de rapport d'erreurs ont cette propriété de contexte.  
  
 Le **BizTalkErrors-SP** envoyer port s’exécute le message d’erreur via un pipeline qui utilise un composant Assembleur XML pour placer le message dans une enveloppe. Le message passe ensuite à l'adaptateur Ops.  
  
 L'enveloppe, définie par le schéma ErrorEnvelope, est marquée pour accepter tout type de message. Toutefois, « tout » signifie tout type de message défini dans le groupe BizTalk. Cela peut entraîner l'interruption des messages si la solution reçoit un message de type inconnu. Un tel message produirait une erreur et qu’il est acheminé vers le **BizTalkErrors-SP** port. À son tour, le message génèrerait une erreur dans le composant Assembleur XML du pipeline car il ne serait pas d'un type connu. L'erreur de pipeline interrompt le message.  
  
> [!NOTE]
>  Pour gérer les erreurs de routage en raison de types de messages inconnus, vous devez écrire un composant de pipeline personnalisé et utiliser le composant dans un pipeline personnalisé pour le **BizTalkErrors-SP** port. Le composant personnalisé remplace le composant Assembleur XML. Votre composant personnalisé doit placer le **/errorreport** propriétés dans l’en-tête de l’enveloppe et ajouter le message dans le corps de l’enveloppe.  
  
 L'adaptateur Ops est un adaptateur d'envoi transactionnel unidirectionnel. Lorsque l'adaptateur traite un message, il commence par charger l'assembly spécifié, si nécessaire. L'adaptateur met des assemblys en mémoire pour éviter la surcharge liée au chargement de l'assembly à chaque appel. Il crée ensuite une instance de la classe spécifiée, puis utilise la réflexion pour obtenir l’objet dans l’assembly qui implémente le **IOpsAIC** interface. Si tout ceci est réussie, l’adaptateur appelle la **initialiser** (méthode), puis appelle la **Execute** méthode, en passant le message de rapport d’erreur.  
  
 S’il existe une erreur appelant **Execute**, l’adaptateur renvoie le message. Si la classe spécifiée n’implémente pas le **IOpsAIC** interface, ou la classe ou l’assembly est introuvable, l’adaptateur interrompt le message.  
  
> [!TIP]
>  Comme l'adaptateur utilise la réflexion, l'assembly contenant la classe doit être dans le Global Assembly Cache.  
  
## <a name="the-iopsaic-interface"></a>Interface IOpsAIC  
 L’adaptateur requiert un objet qui implémente le **IOpsAIC** interface. L'interface apparaît comme suit :  
  
```  
interface IOpsAIC  
{  
    void Initialize(string config);  
    void Execute(byte[] message);  
}  
```  
  
 L’adaptateur transmet le message d’origine en tant que tableau d’octets à la **Execute** (méthode).  
  
## <a name="configuring-the-adapter"></a>Configuration de l'adaptateur  
 Vous configurez l'adaptateur comme vous le feriez pour n'importe quel autre adaptateur. Le tableau suivant décrit ses propriétés de configuration :  
  
|Nom complet| Description|  
|------------------|-----------------|  
|**Nom fort d’assembly .NET**|Le nom complet de l’assembly.|  
|**Classe OpsAIC**|Le nom de la classe dans l’assembly qui implémente le **IOpsAIC** interface.|  
|**Données d’initialisation**|Une chaîne passée en tant qu’argument à la **initialiser** méthode de la classe.|  
  
 Notez que l'adaptateur requiert le nom complet de l'assembly. Le nom complet est le nom donné à un assembly lorsque vous l'ajoutez au Global Assembly Cache. Le nom complet est une chaîne composée du nom de l'assembly, de sa version, de sa culture et d'un jeton de clé publique. Vous pouvez voir les noms complets des assemblys à l'aide de l'outil GAC (gacutil.exe).  
  
 Pour plus d'informations sur les noms complets des assemblys, consultez « Assembly Names » (en anglais) dans le Guide du développeur .NET Framework. Pour plus d'informations sur gacutil.exe, consultez « Global Assembly Cache Tool (Gacutil.exe) » (en anglais) dans le Guide du développeur [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)].  
  
 Vous devez fournir l'espace de noms avec le nom de classe. Par exemple, si la classe est **OpsHandler** dans les **OperationsHandler** espace de noms, vous devez attribuer le nom de classe en tant que **OperationsHandler.OpsHandler**.  
  
## <a name="see-also"></a>Voir aussi  
 [L’adaptateur Ops](../core/the-ops-adapter.md)