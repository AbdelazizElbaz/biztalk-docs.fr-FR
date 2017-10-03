---
title: "Activez Microsoft distribuée transaction coordinator autoriser les transactions pour Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 634538e5-7292-4b3f-85b0-c6db86d0dbd2
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0597c050e1531d71a62af04fe6c825653076297c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="enable-ms-distributed-transaction-coordinator-to-allow-transactions-for-oracle-e-business-suite"></a>Activez Microsoft distribuée transaction coordinator autoriser les transactions pour Oracle E-Business Suite
Configurer MSDTC avant de commencer la création d’applications qui utilisent le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
Les opérations effectuées sur Oracle E-Business Suite à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] (via [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], le modèle de service WCF ou le modèle de canal WCF) peut être effectuée dans une étendue de transaction. Si le programme client possède plusieurs ressources de transaction dans le cadre de la même transaction, la transaction obtient élevés au rang d’une transaction MSDTC. Pour activer la carte effectuer des opérations dans l’étendue d’une transaction MSDTC, configurez MSDTC sur l’ordinateur exécutant le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]et à Oracle E-Business Suite. En outre, ajoutez MSDTC à la liste des exceptions dans votre pare-feu, qui peut être le pare-feu Windows. 
  
> [!NOTE]
>  Les étapes pour configurer MSDTC varient pour les différents systèmes d’exploitation. Les étapes répertoriées dans cette rubrique s’appliquent à des systèmes d’exploitation Windows Server et clients Windows.  
  
## <a name="configure-msdtc"></a>Configurer MSDTC  
  
1.  Ouvrez **Services de composants**.  

    Ou, **le Gestionnaire de serveur**, sélectionnez **outils**, puis sélectionnez **Services de composants**.  
  
2.  Développez **Services de composants**, développez **ordinateurs**, développez **poste**, développez **Distributed Transaction Coordinator**, avec le bouton droit **DTC Local**, puis sélectionnez **propriétés**.  
  
3.  Sélectionnez l'onglet **Sécurité** . Dans cet onglet, sélectionnez tous les éléments suivants : 

  - **Accès DTC réseau**
  - **Autoriser les Clients distants** 
  - **Autoriser les transactions entrantes** 
  - **Autoriser les transactions sortantes** 
  - **Aucun Authetnication requis**
  
4.  Sélectionnez **OK** pour enregistrer vos modifications.  
  
5.  Si vous êtes invité à redémarrer le service MSDTC, sélectionnez **Oui**. Une fois que le service MSDTC est redémarré, fermez les propriétés et la console MMC Services de composants. 
  
## <a name="add-msdtc-to-windows-firewall-exceptions-list"></a>Ajouter de MSDTC à la liste des exceptions du pare-feu Windows  

> [!TIP] 
>  Microsoft Distributed ordre Coordinator (MSDTC) peut déjà être autorisé dans votre pare-feu. Dans ce cas, il est répertorié comme une règle de trafic entrant. S’il n’est pas répertorié, utilisez cette section pour autoriser le MSDTC. 

1.  Ouvrez **pare-feu Windows**, puis sélectionnez **paramètres avancés** sur la gauche.  

    Ou, **le Gestionnaire de serveur**, sélectionnez **outils**, puis sélectionnez **pare-feu Windows avec fonctions avancées de sécurité**.  
  
2.  Bouton droit sur **règles de trafic entrant**, puis sélectionnez **nouvelle règle**.  
  
3.  Dans l’Assistant : 

    1. Sélectionnez **programme**, puis sélectionnez **suivant**. 
    2. Définir le **chemin d’accès du programme** à `%SystemRoot%\system32\msdtc.exe`, puis sélectionnez **suivant**.  
    3. **Autoriser la connexion**, puis sélectionnez **suivant**.
    4. Sélectionnez **domaine**, puis sélectionnez **suivant**.
    5. Entrez un nom quelconque, tel que `MSDTC for Oracle EBS`, puis sélectionnez **Terminer**.
  
5.  Terminez l’Assistant et fermer le pare-feu Windows. 
  
## <a name="next"></a>Suivant 
[Exemples de l’adaptateur Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)