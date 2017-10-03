---
title: "Définir des vues et des activités d’entreprise dans Excel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Excel add-in [BAM], creating business activities
- monitoring business activities [BAM], creating business activities
ms.assetid: 000532f0-cb9a-40ac-a6c5-a8bd4e49f8d0
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91b9d3b213a6a6429759c0bb0d826798afa36da3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="defining-business-activities-and-views-in-excel"></a>Définition des activités et des vues d'entreprise dans Excel
La première étape à effectuer pour créer une solution BAM consiste à identifier les données qui vous intéressent et la manière dont elles doivent être interprétées. Pour ce faire, utilisez le complément BAM pour Excel. Ce complément vous permet d'établir une liste souhaitée des données d'intérêt en définissant une activité d'entreprise. Vous pouvez également définir la manière dont les données doivent être interprétées et affichées pour différentes catégories d'utilisateurs d'activités.  
  
 Le complément BAM vous permet également de définir des agrégations.  
  
 Vous pouvez par ailleurs renommer des éléments d'activité, si la terminologie à laquelle certains utilisateurs sont habitués ne correspond pas aux dénominations des éléments de données correspondants dans l'activité. Par exemple, si la vue est affichée dans une langue différente.  
  
 Une fois la définition des activités terminée, Excel génère des données de prévisualisation de manière aléatoire pour définir les graphiques souhaités, ainsi que d'autres modes de présentation. Pour plus d’informations sur les données d’aperçu, consultez [comment utiliser le tableau croisé dynamique](../core/how-to-use-the-pivottable.md).  
  
 La définition d'activité définit les points de données et les événements qui doivent être collectés lors de l'exécution d'un processus d'entreprise. Vous pouvez obtenir le complément BAM pour Excel à partir de diverses sources.  
  
 Vous pouvez installer le BAM complément XLA lors de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation. Pour plus d’informations, consultez [vue d’ensemble de l’Installation de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)  
  
 L’analyse BAM. XLA est installé dans un des emplacements suivants :  
  
-   Si Microsoft Office n’est pas installé sur l’ordinateur, puis le fichier BAM.xla est installé dans le Files\Microsoft BizTalk Server 20*xx*\ExcelDir\ dossier.  
  
-   Si Microsoft Office est installé, le fichier BAM.xla est installé dans le Files\Microsoft Office\OFFICE*xx*\Library\ dossier.  
  
 Vous pouvez également copier le fichier BAM.xla sur votre ordinateur à partir d'un dossier partagé se trouvant sur un autre ordinateur. Vous pourrez ensuite inscrire le XLA en le sélectionnant à partir de l'emplacement où vous l'avez copié.  
  
 Pour activer le complément BAM dans la barre d’outils du menu Excel, cliquez sur le **fichier** menu, puis cliquez sur **Options**, puis cliquez sur **compléments**. Sélectionnez **Business Activity Monitoring**, puis cliquez sur **accédez**, dans la fenêtre compléments, activez la case à cocher ensuite **Business Activity Monitoring**, puis cliquez sur **OK**.  
  
> [!NOTE]
>  L'utilisation du complément BAM pour Excel exclut la possibilité d'exécuter Excel avec deux instances chargées dans le même processus.  Lors de l'utilisation du complément, plusieurs instances peuvent exister dans le même processus dans les cas suivants :  
>   
>  Lorsqu'une feuille de calcul Excel est ouverte, avec le complément BAM activé, et que vous double-cliquez sur une feuille de calcul Excel différente, Excel tente de charger la feuille de calcul dans l'instance en cours d'exécution.  
>   
>  Lorsqu'une feuille de calcul Excel est ouverte, avec le complément BAM activé, et que vous utilisez l'option de menu Fichier/Ouvrir pour charger une autre feuille de calcul Excel.  
  
 Ces situations ne vous permettent pas d'utiliser correctement le complément BAM. Pour ouvrir plusieurs feuilles de calcul Excel lorsque le complément BAM est activé, vous devez ouvrir une nouvelle copie d'Excel et charger la feuille de calcul dans cette instance d'Excel.  
  
> [!NOTE]
>  Lorsque vous utilisez BAM.xla dans Excel, vous pouvez obtenir l’erreur « ce classeur a perdu son projet VBA, contrôles ActiveX et autres fonctionnalités liées à la programmabilité. » Pour plus d’informations sur l’erreur, consultez [BAM de dépannage](../core/troubleshooting-bam.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [La définition d’une activité d’entreprise](../core/how-to-define-a-business-activity.md)  
  
-   [Définition d’une vue BAM](../core/defining-a-bam-view.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse des activités d’entreprise avec BAM](../core/monitoring-business-activities-with-bam.md)