---
title: "Recommandations de sécurité d’exécution BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, runtime
- runtime, security
- discretionary access control lists (DACLs)
- DACLs
- .NET Framework Code Access Security Mechanism
ms.assetid: 1933789d-b79a-47ad-8f70-6f1e99bc2be0
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27386b7294294088b7dcfcad1198e410e56e724d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-server-runtime-security-recommendations"></a>Recommandations de sécurité d’exécution BizTalk Server
Vous devez installer le composant d'exécution de BizTalk Server (ou moteur) sur tous les ordinateurs à partir desquels vous souhaitez recevoir, envoyer, traiter et suivre des messages. En d'autres termes, vous devez installer les composants d'exécution sur les ordinateurs sur lesquels vous créez une instance d'hôte BizTalk (serveurs de traitement). Il est conseillé de suivre les recommandations suivantes pour sécuriser et déployer le composant d'exécution de BizTalk Server dans votre environnement.  
  
-   Assurez-vous de disposer des autorisations de sécurité minimales pour effectuer les tâches d'exécution BizTalk. Pour plus d’informations sur les autorisations de sécurité minimales, consultez [autorisations de sécurité minimales](../core/minimum-security-user-rights.md).  
  
    > [!NOTE]
    >  La configuration de BizTalk fournit aux comptes les autorisations minimales dont ils ont besoin pour effectuer leurs tâches.  
  
-   Le compte de service des instances d'hôte doit ouvrir une session en tant que service sur l'ordinateur exécutant l'instance d'hôte.  
  
-   Seuls le ou les comptes de service d'un hôte ont accès aux données MessageBox associées à un hôte. En outre, seuls ces services sont autorisés à publier des données dans la base de données MessageBox. Pour diminuer les risques d'attaque liée à la divulgation d'informations, il est déconseillé d'utiliser le même compte de service pour plusieurs hôtes.  
  
-   Les serveurs de traitement (hôtes n'hébergeant pas le suivi) doivent uniquement se connecter aux bases de données MessageBox et de gestion, ainsi qu'au serveur de secret principal. Si vous utilisez la sécurité du protocole Internet (IPSec), vous pouvez limiter leur accès aux deux bases de données et au serveur de secret principal.  
  
-   Tous les composants exécutés au sein du même hôte BizTalk ont un niveau de confiance identique à celui de l'hôte. Il revient à l'administrateur BizTalk de déterminer les composants qui sont exécutés sous un hôte donné et partagent le même niveau de confiance. BizTalk fait en sorte que les seuls assemblys installés par des administrateurs BizTalk soient exécutés sous un hôte BizTalk. Si vous souhaitez définir d'autres restrictions relatives aux composants utilisés par les assemblys BizTalk (par exemple, pour exécuter des assemblys signés par un fournisseur particulier ou valider la signature de nom fort d'une orchestration), vous pouvez utiliser le mécanisme de sécurité d'accès du code [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]. Pour plus d’informations sur le site Web Microsoft MSDN à l’adresse [http://go.microsoft.com/fwlink/?LinkId=60947](http://go.microsoft.com/fwlink/?LinkId=60947).  
  
-   La granularité des autorisations relatives à la publication des messages est définie au niveau de l'hôte BizTalk. En d'autres termes, si vous exécutez plusieurs orchestrations ou adaptateurs au sein d'un hôte BizTalk, vous ne pouvez pas limiter la réception des messages envoyés à l'hôte à une orchestration spécifique.  
  
-   Lorsqu'un hôte n'est pas autorisé à recevoir un message, il le place dans sa file d'attente de messages interrompus. Par défaut, lorsque des adaptateurs de réception et des orchestrations sont exécutés sur un même hôte, l'orchestration peut lire la file d'attente de messages interrompus de l'hôte et récupérer un message interrompu par BizTalk en raison d'un échec d'autorisation. Pour cette raison, il est déconseillé d'exécuter des orchestrations et des adaptateurs de réception sur le même hôte.  
  
-   Les instances d'hôte sont des services Windows exécutés sur un ordinateur spécifique. Pour créer une instance d'hôte, vous devez être un administrateur BizTalk et un administrateur Windows sur l'ordinateur sur lequel vous souhaitez créer l'instance d'hôte, car BizTalk crée un service Windows correspondant à l'instance d'hôte.  
  
-   Lorsque Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] génère un assembly, il utilise une clé personnalisée créée par l'interface IDE (Integrated Developer Environment). Si votre environnement requiert la signature de tous les assemblys associés à une clé spécifique, vous devez configurer l'utilisation de cette clé ou de la temporisation de la signature des assemblys dans l'interface IDE de tous les ordinateurs de développement.  
  
-   Les composants des pipelines de réception et d'envoi tentent de minimiser l'encombrement mémoire. Lorsque la taille des données dépasse un seuil défini, ces composants transmettent des données en continu vers le dossier temporaire (%TEMP%) du disque. Vous devez vous assurer que les dossiers temporaires associés aux comptes de service des instances d'hôte disposent des listes de contrôle d'accès discrétionnaire (DACL) adéquates afin que le seul compte de service soit autorisé à lire ces fichiers. Vous devez également veiller à ce que le dossier temporaire dispose de l'espace nécessaire au stockage de fichiers potentiellement volumineux.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de la sécurité de BizTalk Server](../core/managing-biztalk-server-security.md)   
 [Ports pour les serveurs de traitement](../core/ports-for-the-processing-servers.md)   
 [Recommandations de sécurité pour un déploiement BizTalk Server](../core/security-recommendations-for-a-biztalk-server-deployment.md)   
 [Planification de la sécurité](../core/planning-for-security.md)