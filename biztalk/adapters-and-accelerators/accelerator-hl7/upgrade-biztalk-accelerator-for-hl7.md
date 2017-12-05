---
title: "Mise à niveau de BizTalk Accelerator pour HL7 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91b6747f-e560-4cf8-99b5-af0d150599bf
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d4df85c965943f2f2c916fef6b558f98caf2175f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="upgrade-biztalk-accelerator-for-hl7"></a>Mise à niveau de BizTalk Accelerator pour HL7
Vue d’ensemble de la [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] mise à niveau. 
  
<a name="BKMK_BeforeUpgrade"></a>   
## <a name="before-you-upgrade"></a>Avant la mise à niveau  
  
-   L’utilisateur qui exécute la mise à niveau doit être membre du groupe Administrateurs de BizTalk.  
  
-   Le service SQL Server (MSSQLSERVER) doit être en cours d’exécution lorsque vous effectuez une mise à niveau.  
  
-   N’exécutez pas une installation sans assistance pour mettre à niveau.  
  
-   Lorsque vous mettez à niveau, le programme d’installation migre existants [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] informations de configuration à une version plus récente.  
  
-   Lorsque vous mettez à niveau, les clés de Registre et les bases de données sont automatiquement sauvegardés.  
  
-   Les fichiers dans le  *\<lecteur\>*: \Program Files\Microsoft BizTalk \<version\> Accelerator pour HL7 dossier sont mises à jour.  
  
> [!IMPORTANT]
>  La mise à niveau ne crée pas un nouveau dossier pour les fichiers mis à niveau, et il modifie le nom du dossier existant.  
  
<a name="BKMK_UpgradePaths"></a>   
## <a name="supported-upgrade-paths"></a>Chemins de mise à niveau pris en charge  
 Le tableau suivant répertorie la prise en charge [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] versions qui peuvent être mis à niveau. « Oui » signifie que le [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] version peut être mise à niveau. « Non » signifie que le [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] version ne peut pas être mise à niveau. Si le [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] version n’est pas répertoriée, cette version ne peut pas être mis à niveau.  

||[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]|[!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)]|BizTalk Server 2013|
|---|---|---|---|  
|[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 2013|Oui|Oui|Non|  
|[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 2010|Non|Oui|Oui|  

<a name="BKMK_UpgradeSteps"></a>   
## <a name="upgrade-steps"></a>Étapes de mise à niveau  
  
1.  Mettre à niveau le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].   
  
2.  Sauvegardez le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] bases de données et votre HL7 des schémas de message.  
  
3.  Sauvegardez tous les fichiers sous le   ***\<lecteur\>*: \Program Files\Microsoft BizTalk Accelerator pour HL7** dossier que vous avez modifiés. Par exemple, sauvegardez les fichiers dans le Kit de développement logiciel.  
  
4.  Installer la mise à jour appropriée pour votre version de [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]:  
  
    -   Si la mise à niveau à partir de BTAHL7 2010, installez **HL72010Patch.msp**.  
  
    -   Si la mise à niveau à partir de BTAHL7 2013, installez **HL72013Patch.msp**.  
    
  
5.  Exécutez le [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] le programme d’installation. Consultez [installer BizTalk Accelerator pour HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md).  
  
6.  Déployer la nouvelle BTAHL7V2*x*projet Common.  
  
7.  Redéployer tous les autres assemblys.  
  
8.  Regénérez les projets ou les assemblys qui contiennent une référence à un ou plusieurs assemblys [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]. À l’aide de **BTSTask.exe** dans \< *lecteur*\>: \Program Files\Microsoft BizTalk Server \<version\>manuellement redéployer ces projets.  
  
9. Redémarrez le service [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] .  
  
<a name="BKMK_UpgradeMulti"></a>   
## <a name="upgrading-in-a-multi-server-environment"></a>La mise à niveau dans un environnement multiserveur  
 Dans un multi-serveur [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] environnement, de mise à niveau tous les [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]s et la mise à niveau puis le [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] sur tous les serveurs. Migrez vos serveur dans l'ordre suivant :  
  
-   Le serveur hébergeant le groupe BizTalk  
  
-   Chaque nœud de traitement  
  
-   Le serveur du portail BAM  
  
## <a name="see-also"></a>Voir aussi  
 [Installer BizTalk Accelerator pour HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md)