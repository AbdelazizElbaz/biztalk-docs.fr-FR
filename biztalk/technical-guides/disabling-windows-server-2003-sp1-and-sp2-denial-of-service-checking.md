---
title: "La désactivation de Windows Server 2003 SP1 et SP2 des attaques de déni de Service de la vérification de la | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8822c1e4-d146-4361-b25a-7b81cd5cdd3b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b33333efd055a659557513ecc8e0b53a42bc30ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="disabling-windows-server-2003-sp1-and-sp2-denial-of-service-checking"></a>La désactivation de Windows Server 2003 SP1 et SP2 des attaques de déni de Service de la vérification de la
> [!NOTE]  
>  Cette rubrique s’applique uniquement pour Windows Server 2003.  
  
 Vous devez désactiver le refus de Windows Server 2003 Service Pack 1 et Service Pack 2 de vérification du service. Il s’agit, car dans certains cas de forte charge, Windows Server 2003 SP1 et SP2 déni de service recherche peut identifier de manière incorrecte les connexions TCP/IP valides comme une attaque par déni de service.  
  
> [!IMPORTANT]  
>  Vous devez désactiver cette fonction uniquement dans un scénario intranet lorsque vous êtes sûr que vous ne seront pas affectées à partir de réel attaques par déni de service.  
  
## <a name="how-denial-of-service-can-affect-tcpip-connections"></a>Comment les attaques de déni de Service peuvent affecter les connexions TCP/IP  
 Windows Server 2003 SP1 et SP2 implémentent une fonctionnalité de sécurité qui réduit la taille de la file d’attente pour les connexions TCP/IP simultanées au serveur. Ce composant a pour but d'empêcher les attaques de type refus de service. Conditions de charge importante, le protocole TCP/IP dans Windows Server 2003 SP1 ou version ultérieure peut identifier de manière incorrecte les connexions TCP/IP valides comme une attaque par déni de service. Cela peut se produire lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est surchargé.  
  
## <a name="modifying-the-registry-entry"></a>Modification de l’entrée de Registre  
 Pour plus d’informations, consultez l’article de la Base de connaissances Microsoft 899599, [« une instance d’hôte BizTalk Server échoue et une erreur de « Réseau générale » est consignée dans le journal des applications lorsque le serveur BizTalk Server traite un volume important de documents » ](http://go.microsoft.com/fwlink/?LinkId=158860) (http://go.microsoft.com/fwlink/?LinkId=158860). Suivez les instructions de cet article pour créer le **SynAttackProtect** entrée de Registre sur les ordinateurs exécutant SQL Server qui hébergent [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données et sur tous les ordinateurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui exécutent Windows Server 2003 SP1 ou version ultérieure.  
  
## <a name="tuning-registry-settings-that-govern-the-level-of-denial-of-service-attack-protection"></a>Réglage des paramètres de Registre qui régissent le niveau de refus de la protection contre les attaques de Service  
 Dans certains scénarios, vous souhaiterez refus de protection de service sont conservées, mais réduit la rapidité avec laquelle le refus d’une fonctionnalité de service est appliqué. Il est possible de paramétrer le comportement par défaut du refus de la fonctionnalité de protection de service en procédant comme suit :  
  
1.  Vérifiez que le **SynAttackProtect** entrée de Registre est définie sur une valeur REG_DWORD de **1** comme décrit dans [http://go.microsoft.com/fwlink/?LinkId=111477](http://go.microsoft.com/fwlink/?LinkId=111477).  
  
2.  Configurer le **TcpMaxHalfOpen** entrée de Registre comme décrit dans [http://go.microsoft.com/fwlink/?LinkId=111478](http://go.microsoft.com/fwlink/?LinkId=111478).  
  
3.  Configurer le **TcpMaxHalfOpenRetried** entrée de Registre comme décrit dans [http://go.microsoft.com/fwlink/?LinkId=111479](http://go.microsoft.com/fwlink/?LinkId=111479).  
  
## <a name="see-also"></a>Voir aussi  
 [Listes de vérification de disponibilité opérationnelle](../technical-guides/operational-readiness-checklists.md)