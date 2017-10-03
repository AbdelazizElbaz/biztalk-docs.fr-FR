---
title: Configurer MSDTC sur le client de SQL Server et de carte | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c87f455-a8c4-4169-bf18-695926136df1
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf519044dc28d417d85682189dd4a52585310ac0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-msdtc-on-sql-server-and-adapter-client"></a>Configurer MSDTC sur un client SQL Server et de la carte
Les opérations effectuées sur l’utilisation de SQL Server le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] (via [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], le modèle de service WCF ou le modèle de canal WCF) peut être effectuée dans une étendue de transaction. Si le programme client possède plusieurs ressources de transaction dans le cadre de la même transaction, la transaction obtient élevés au rang d’une transaction MSDTC. Pour activer la carte effectuer des opérations dans l’étendue d’une transaction MSDTC, vous devez configurer MSDTC à la fois sur l’ordinateur exécutant le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] et SQL Server. En outre, vous devez ajouter MSDTC à la liste des exceptions du pare-feu Windows. Cette section fournit des informations sur comment effectuer ces tâches sur les ordinateurs exécutant le client de l’adaptateur et le SQL Server.  
  
> [!NOTE]
>  Exécution d’opérations sur l’utilisation de SQL Server [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] toujours implique deux ressources, l’adaptateur de la connexion à SQL Server et de la boîte de Message BizTalk résidant sur SQL Server. Par conséquent, toutes les opérations effectuées à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] sont effectuées dans l’étendue d’une transaction MSDTC. Par conséquent, pour utiliser le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous devez toujours activer MSDTC.  
  
> [!NOTE]
>  Pour les opérations où le client de carte n’écrit pas toutes les données à la base de données SQL Server, tel qu’une opération Select, vous pouvez la charge supplémentaire d’effectuer les opérations à l’intérieur d’une transaction. Dans ce cas, vous pouvez configurer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour effectuer des opérations sans un contexte transactionnel en définissant le **UseAmbientTransaction** liaison de propriété **false**. Pour plus d’informations sur la propriété de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md). Dans ce cas, il est inutile de configurer MSDTC ainsi.  
  
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
  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications SQL](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)