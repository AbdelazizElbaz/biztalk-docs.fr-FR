---
title: "Scénario de faible latence Optimizations1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd2a891a-ee4b-4542-b3ce-434e2a6474be
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12f16f67f1c161f74e6a9179db8c85f48b5b3e14
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="low-latency-scenario-optimizations"></a>Optimisations de scénario de faible latence
Par défaut, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est optimisé pour le débit plutôt que de faible latence. Les optimisations suivantes ont été appliquées à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour le scénario de test utilisé dans ce guide.  
  
> [!NOTE]  
>  Ces optimisations améliorent les temps de latence, mais peuvent le faire à un coût pour le débit global.  
  
## <a name="increase-the-biztalk-server-host-internal-message-queue-size"></a>Augmenter la taille de file d’attente de messages interne hôte BizTalk Server  
 Chaque hôte de BizTalk possède sa propre file d’attente en mémoire interne. Augmenter la taille de cette file d’attente à partir de la valeur par défaut de 100 à 1000 pour améliorer les performances d’un scénario à faible latence. Pour plus d’informations sur la modification de la valeur de la taille de file d’attente de messages interne, consultez « Comment pour modifier les paramètres par défaut hôte limitation » dans l’aide de BizTalk Server à [http://go.microsoft.com/fwlink/?LinkID=120225](http://go.microsoft.com/fwlink/?LinkID=120225).  
  
## <a name="reduce-the-maxreceiveinterval-value-in-the-admserviceclass-table-of-the-biztalk-server-management-database"></a>Réduisez la valeur MaxReceiveInterval dans la table adm_ServiceClass de la base de données de gestion BizTalk Server  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]utilise un mécanisme d’interrogation pour recevoir des messages à partir de ses files d’attente de l’ordinateur hôte dans la Messagebox. Le **MaxReceiveInterval** valeur dans la table adm_ServiceClass de la base de données de gestion BizTalk (BizTalkMgmtDb) est la valeur maximale, en millisecondes que chaque instance d’hôte BizTalk doit attendre jusqu'à ce qu’il interroge la MessageBox. La table adm_ServiceClass contient un enregistrement pour les types de service suivants :  
  
-   **XLANG/S** – pour les instances d’hôte d’orchestration BizTalk  
  
-   **Messagerie InProcess** – pour les instances d’hôte in-process  
  
-   **MSMQT** – pour les instances d’hôte adaptateur MSMQT  
  
-   **Messagerie isolée** – pour hors des instances d’hôte de processus, utilisés par le protocole HTTP, SOAP et certaine WCF gestionnaires d’adaptateur de réception  
  
 Par défaut, cette valeur est définie à 500 millisecondes, qui est optimisé pour un débit plutôt que de faible latence. Dans certains scénarios, la latence peut être améliorée en réduisant cette valeur.  
  
> [!NOTE]  
>  Modifications apportées à cette valeur avoir un impact sur toutes les instances du type de service associé, par conséquent, prenez soin d’évaluer l’impact sur toutes les instances d’hôte avant de modifier cette valeur.  
  
> [!NOTE]  
>  Cette valeur est utilisée uniquement si la Messagebox n’a aucun message non traité restants. S’il existe une constante en retard de traitement de messages non traités dans la Messagebox, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tente de traiter les messages sans en attente sur le délai d’interrogation. Une fois que tous les messages sont traités, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] commencera interrogation à l’aide de la valeur spécifiée pour MaxReceiveInterval.  
  
> [!NOTE]  
>  Dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement avec un ratio élevé des instances d’hôte pour les instances de base de données Messagebox, la diminution de la valeur pour MaxReceiveInterval peut provoquer l’utilisation excessive du processeur sur l’ordinateur SQL Server qui héberge l’instance de base de données Messagebox. Par exemple, si la MaxReceiveInterval est réduite à une valeur faible (\< 100) dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement avec une seule Messagebox et les instances d’hôte > 50, l’utilisation du processeur sur le serveur SQL Server peut excéder 50 %. Ce phénomène peut se produire, car la surcharge liée à l’interrogation en permanence les files d’attente de l’hôte est significative. Si vous réduisez MaxReceiveInterval à une valeur inférieure à 100, vous devez également évaluer l’impact sur l’utilisation du processeur de votre ordinateur SQL Server.