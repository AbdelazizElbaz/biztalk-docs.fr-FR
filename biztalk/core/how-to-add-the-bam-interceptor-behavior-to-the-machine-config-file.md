---
title: "Comment ajouter le comportement de l’intercepteur BAM au fichier Machine.config | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ea09925-264f-4976-8e34-f63bad70f886
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: abc8845333389c95ea52d440437935d4c4867dc1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-the-bam-interceptor-behavior-to-the-machineconfig-file"></a>Ajout du comportement de l'intercepteur BAM au fichier Machine.config
Pour intercepter des données dans l'analyse BAM, vous devez ajouter le comportement d'intercepteur BAM au fichier machine.config Microsoft .NET. Pour ce faire, deux possibilités :  
  
-   modifier manuellement le fichier machine.config pour inclure le comportement ;  
  
-   utiliser l'éditeur de configuration de service pour inclure le comportement.  
  
### <a name="to-manually-edit-the-machineconfig-file"></a>Pour modifier manuellement le fichier machine.config  
  
1.  Modifiez le fichier machine.config situé dans le dossier de configuration Microsoft .NET. Pour ce faire, cliquez sur **Démarrer**, cliquez sur **exécuter**, tapez notepad c:\WINDOWS\Microsoft.NET\Framework\v4.0.30319\Config\machine.config, puis cliquez sur **OK**.  
  
2.  Mettez à jour le fichier machine.config avec les extensions de comportement suivantes.  
  
    ```  
    <system.serviceModel>  
      <extensions>  
        <behaviorExtensions>  
          <add name="BAMEndPointBehaviorExtension" type="Microsoft.BizTalk.Bam.Interceptors.Wcf.BamEndpointBehavior, Microsoft.BizTalk.Bam.Interceptors, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
        </behaviorExtensions>  
      </extensions>  
    </system.serviceModel>  
    ```  
  
3.  Fermez et enregistrez le fichier machine.config.  
  
#### <a name="to-edit-the-machineconfig-file-using-the-service-configuration-editor"></a>Pour modifier le fichier machine.config à l'aide de l'éditeur de configuration de service  
  
1.  Ouvrez l'éditeur de configuration de service. Pour plus d’informations sur l’utilisation de l’éditeur de Configuration de Service, consultez [http://go.microsoft.com/fwlink/?LinkId=83557](http://go.microsoft.com/fwlink/?LinkId=83557).  
  
2.  Dans le volet d’arborescence (étiqueté **Configuration**), développez l’arborescence de nœuds. Cliquez sur le **avancé** dossier, cliquez sur le **Extensions** dossier, puis sélectionnez le **extensions d’élément de comportement** élément.  
  
3.  Créez une extension d'élément de comportement. Cliquez sur le **nouveau** bouton pour ouvrir la boîte de dialogue Éditeur de Configuration d’élément d’Extension. Dans **nom de la Configuration** Entrez un nom unique pour le comportement, par exemple BAMEndPointBehaviorExtension.  
  
     ![Éditeur de Configuration d’élément d’extension](../core/media/00a053ba-1993-4e52-a336-e452cc60691c.gif "00a053ba-1993-4e52-a336-e452cc60691c")  
  
4.  Cliquez sur le **Type** champ, puis cliquez sur le bouton de sélection (**...** ) pour ouvrir la boîte de dialogue Explorateur de Type Extension de comportement.  
  
5.  Cliquez sur l'icône Global Assembly Cache (GAC) pour répertorier les DLL dans le GAC.  
  
6.  Sélectionnez l'assembly Microsoft.BizTalk.Bam.Interceptors.  
  
7.  Cliquez sur le **ouvrir** bouton pour sélectionner l’assembly, puis fermez la boîte de dialogue.  
  
     ![Extensions Bejavopr](../core/media/0d525d4c-927c-42d6-96b7-0ebaf2691c6c.gif "0d525d4c-927c-42d6-96b7-0ebaf2691c6c")  
  
8.  Dans le volet Nom du type de la boîte de dialogue Explorateur de types d'extension de comportement, double-cliquez sur le type Microsoft.BizTalk.Bam.Interceptors.Wcf.BamEndpointBehavior (mis en surbrillance dans l'écran suivant).  
  
     ![Extensions Bejavopr](../core/media/67186ad6-8802-4214-be46-11e50e4ff15d.gif "67186ad6-8802-4214-be46-11e50e4ff15d")  
  
     Ceci permet d'ouvrir l'éditeur des éléments de configuration d'extension.  
  
9. Cliquez sur **OK** pour fermer la boîte de dialogue Éditeur de Configuration d’élément d’Extension.  
  
10. Dans le volet Détails de l'éditeur de configuration de service, vérifiez que BAMEndPointBehaviorExtension apparaît.  
  
11. Fermez l'éditeur de configuration de service.  
  
## <a name="next-steps"></a>Étapes suivantes  
 [Comment configurer l’Interception WCF BAM](../core/how-to-configure-the-bam-wcf-interception.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur WCF pour intercepter les données BAM](../core/configuring-the-wcf-adapter-to-intercept-bam-data.md)