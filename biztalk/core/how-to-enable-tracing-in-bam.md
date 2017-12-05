---
title: "Comment activer le suivi de l’analyse BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4da99e74-a41d-4ab1-a07d-e3bee6187216
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 084eaf8cd4ba1c251b1c196830f76ef9c6a8e33f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-enable-tracing-in-bam"></a>Activation du suivi dans BAM
Vous pouvez activer le suivi dans BAM afin de faciliter la résolution des problèmes susceptibles de survenir dans les cinq composants BAM suivants :  
  
-   utilitaire de gestion de l'analyse BAM  
  
-   Bus d'événements BAM  
  
-   Portail BAM  
  
-   La génération d’alertes BAM  
  
-   Intercepteur WCF BAM  
  
## <a name="enabling-tracing-for-the-bam-management-utility"></a>Activation du suivi pour l'utilitaire de gestion de l'analyse BAM  
 En activant le suivi de cet utilitaire, vous pouvez récupérer des informations sur les échecs de déploiement. Pour cela, de deux manières. activer le suivi depuis la ligne de commande pour certaines commandes BM.exe, ou modifier le fichier de configuration de l'utilitaire de gestion de l'analyse BAM afin d'activer le suivi, pour toutes les commandes BM.exe.  
  
### <a name="using-the-command-line"></a>Utilisation de la ligne de commande  
 Le suivi de ligne de commande BM.exe est activé à l’aide de la **-Trace : sur &#124; off** basculer. L'utilisation de l'option Trace remplace les paramètres du fichier de configuration.  
  
 L'option est utilisée conjointement avec toute commande BM.exe classique.  
  
 Exemple :  
  
 **BM.exe déployer-all - DefinitionFile:PO.xml – Trace : sur**  
  
### <a name="using-the-configuration-file"></a>Utilisation du fichier de configuration  
 Vous pouvez activer le suivi en modifiant le fichier de configuration BM.exe.config situé dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking. Ce fichier contient un **system.diagnostics** section qui contient les éléments de suivi. Supprimez les commentaires pour activer le suivi. Par défaut, le suivi est désactivé.  
  
 `<system.diagnostics>`  
  
 `<!-- To turn on BAM tracing, remove this comment or use the "-trace:on" command-line switch`  
  
 `<switches>`  
  
 `<add name="bm" value="1" />`  
  
 `<add name="Microsoft.BizTalk.Bam.Management" value="1" />`  
  
 `</switches>`  
  
 `-->`  
  
## <a name="enabling-tracing-for-the-bam-event-bus"></a>Activation du suivi pour le bus d'événements BAM  
 L'activation du suivi pour le bus d'événements BAM peut vous permettre de diagnostiquer deux catégories d'erreurs de stockage de base de données :  
  
-   les erreurs issues d'événements du service BizTalk Server lors de l'utilisation de l'Éditeur de modèle de suivi ;  
  
-   les erreurs générées lors de l'utilisation des API de flux d'événements mis en mémoire tampon.  
  
 Pour activer le suivi pour le bus d'événements BAM, modifiez ou ajoutez la section suivante du fichier BTSNTSvc.exe.config situé dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].  
  
 `<system.diagnostics>`  
  
 `<switches>`  
  
 `<add name="Microsoft.BizTalk.Bam.EventBus" value="1" />`  
  
 `</switches>`  
  
 `<trace autoflush="true" indentsize="4">`  
  
 `<listeners>`  
  
 `<add name="Text" type="System.Diagnostics.TextWriterTraceListener" initializeData="c:\tdds.log"/>`  
  
 `</listeners>`  
  
 `</trace>`  
  
 `</system.diagnostics>`  
  
#### <a name="to-enable-tracing-for-the-bam-event-bus"></a>Pour activer le suivi pour le bus d'événements BAM  
  
1.  Modifiez le fichier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BTSNTSvc.exe.config.  
  
2.  Recherchez le \<system.diagnostics\> et \</System.Diagnostics\> balise. Si vous ne les trouvez pas dans le fichier, copiez le code indiqué plus haut et collez-le dans le fichier de configuration.  
  
3.  Supprimez les marques de commentaires que les diagnostics système section en plaçant le délimiteur de commentaire de fin ('-->') d’après le \</System.Diagnostics\> balise avant le \<system.diagnostics\> balise.  
  
4.  Enregistrez le fichier.  
  
## <a name="enabling-tracing-for-the-bam-portal"></a>Activation du suivi pour le portail BAM  
 L'activation du suivi pour le portail BAM vous permet de résoudre les problèmes de connectivité.  
  
 Le portail BAM est une application ASP.NET qui suit le protocole standard de suivi. Dans le [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]bamportal\web.config, fichier, il existe une section intitulée \<trace\> que vous pouvez activer.  
  
#### <a name="to-enable-tracing-for-the-bam-portal"></a>Pour activer le suivi pour le portail BAM  
  
1.  Modifiez le fichier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config.  
  
2.  Recherchez le \<system.diagnostics\> et \</System.Diagnostics\> balises.  
  
3.  Supprimez les commentaires de la section des diagnostics système par déplacement délimiteur de commentaire de fin ('-->') d’après le \</System.Diagnostics\> balise avant le \<system.diagnostics\> balise.  
  
4.  Modifiez l'attribut initializeData afin d'indiquer l'emplacement d'écriture du journal des suivis.  
  
5.  Recherchez \<system.web\> balise.  
  
6.  Dans la section system.web, repérez la balise de suivi et supprimez les marques de commentaires de la commande trace en plaçant le délimiteur ('-->'), placé après la balise de suivi, devant la balise.  
  
7.  Enregistrez le fichier.  
  
 `<!--`  
  
 `TRACING: To turn tracing on:`  
  
 `1) Uncomment this tag and specify a file path for trace output`  
  
 `2) Uncomment the <trace tag> under <system.web>`  
  
 `The trace will be saved to the file pointed to by "initializeData" below.`  
  
 `Ensure that the target directory exists (C:\temp by default).`  
  
 `Make sure that the IIS worker process user account (usually Network Service or ASPNET)`  
  
 `and the BAM Portal user have write permissions for the trace log file directory (C:\temp below).`  
  
 `To turn tracing on, you will need to uncomment the <trace> tag under <system.web>`  
  
 `<system.diagnostics>`  
  
 `<trace autoflush="true" indentsize="2">`  
  
 `<listeners>`  
  
 `<add name="BAMPortalListener"`  
  
 `type="System.Diagnostics.TextWriterTraceListener"`  
  
 `initializeData="C:\temp\BAMPortalTrace.log" />`  
  
 `</listeners>`  
  
 `</trace>`  
  
 `</system.diagnostics>`  
  
 `-->`  
  
 `<!--`  
  
 `TRACING: To turn tracing on:`  
  
 `1) Uncomment this tag`  
  
 `2) Uncomment the <system.diagnostics> tag above and specify a file path for trace output`  
  
 `<trace enabled="true"`  
  
 `requestLimit="40"`  
  
 `pageOutput="false"`  
  
 `traceMode="SortByTime"`  
  
 `localOnly="true"`  
  
 `writeToDiagnosticsTrace="true" />`  
  
 `-->`  
  
## <a name="bam-alerting"></a>Alertes BAM  
 L'activation du suivi pour les alertes BAM vous permet de résoudre les erreurs de notification d'alertes.  
  
 La fonction d'alertes BAM repose sur l'infrastructure des services de notification de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Pour activer le suivi des alertes BAM, consultez Résolution des problèmes de rubriques sur les Services de Notification [http://go.microsoft.com/fwlink/?LinkId=79416](http://go.microsoft.com/fwlink/?LinkId=79416).  
  
## <a name="bam-interceptors"></a>Intercepteurs BAM  
 Pour activer le suivi de bout en bout des intercepteurs BAM, modifiez le fichier de configuration de l'application : le fichier Web.config pour les applications hébergées sur le Web, ou le fichier Appname.config pour les applications auto-hébergées. L'exemple suivant illustre la modification du fichier :  
  
```  
<system.diagnostics>  
  </sources>  
    <source name="Microsoft BizTalk Bam Interceptors" switchValue="All">  
      <listeners>  
  
        <add name="myListener"  
             type="System.Diagnostics.TextWriterTraceListener"  
             initializeData="TextWriterOutput.log" />  
      </listeners>  
    </source>  
  </sources>  
</system.diagnostics>  
```  
  
 Les intercepteurs BAM de Windows Workflow Foundation et Windows Communication Foundation sont écrits dans la source nommée « Microsoft BizTalk Bam Interceptors ».  
  
> [!NOTE]
>  La chaîne de la source distingue les majuscules et les minuscules et doit donc apparaître exactement comme indiqué. Dans le cas contraire, vous ne pourrez pas recevoir les informations de suivi des intercepteurs BAM.  
  
 La définition du paramètre switchValue permet de contrôler le niveau de suivi. Le tableau suivant récapitule les différents niveaux de suivi disponibles.  
  
|Niveau de suivi| Description|  
|-----------------|-----------------|  
|Critique|Consigne les entrées Fail-Fast et Event Log, ainsi que les informations de corrélation de suivi.|  
|Erreur|Consigne toutes les exceptions.|  
|Avertissement|Condition susceptible de générer une erreur ou une erreur critique.|  
|Informations|Des messages utiles au contrôle et au diagnostic de l'état du système, à l'évaluation des performances ou au profil sont générés. Utilisez-les pour la planification de capacité et la gestion des performances.|  
|Commentaires|Suivi de niveau débogage pour le traitement et le code utilisateur.|  
|Tous|Tous les messages.|  
  
> [!NOTE]
>  Le suivi peut nuire aux performances. Ne l'activez donc que dans le cadre de résolution de problèmes.  
  
### <a name="viewing-the-wcf-trace-file"></a>Affichage du fichier de suivi WCF  
 Utilisez l'outil WCF Service Trace Viewer pour analyser le suivi WCF. Pour plus d’informations sur l’outil Service Trace Viewer, consultez [http://go.microsoft.com/fwlink/?LinkId=75218](http://go.microsoft.com/fwlink/?LinkId=75218).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de l’analyse BAM](../core/managing-bam.md)