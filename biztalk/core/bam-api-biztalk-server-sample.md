---
title: "L’API BAM (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, APIs
- examples, BAM
- BAM, examples
- APIs, BAM
ms.assetid: 32a925f2-c7f4-4111-9c59-8865f15c6a89
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c9953bb5e8b1e9827189e5b618f2760297c5678
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-api-biztalk-server-sample"></a>API BAM (exemple BizTalk Server)
L'exemple API BAM montre comment incorporer des appels à l'API BAM dans une application pour enregistrer des informations clés que vous pouvez surveiller.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple implémente un scénario d'achat simple. Il génère des bons de commande, traite chaque bon de commande, crée des expéditions et crée et traite des factures. Pendant son exécution, l'exemple crée et met à jour des activités BAM pour refléter les détails et la disposition des bons de commande et des factures.  
  
## <a name="how-this-sample-was-designed-and-why"></a>Conception et finalité de cet exemple  
 Cet exemple a été conçu pour illustrer l'utilisation de l'analyse BAM pour stocker des informations d'une application qui n'est pas une orchestration BizTalk. Lorsque l'application est simple, il montre les différents aspects de BAM que vous pourriez utiliser dans une application de production. Ces options en question sont les suivantes :  
  
-   Plusieurs threads qui contribuent à une activité unique  
  
-   Création d'une relation entre deux activités  
  
-   Utilisation d'une continuation pour permettre l'accès à la même activité avec différents ID  
  
 L’exemple API BAM se compose de trois classes principales : une pour traiter des bons de commandes, une pour traiter les expéditions et une pour traiter les factures. Chaque classe a un **RunOnce** méthode extrait un message d’une file d’attente, puis traite le message. Chaque classe a également un **exécuter** méthode qui appelle continuellement la **RunOnce** (méthode).  
  
 Le **RunOnce** méthode de la **PoApplication** classe effectue les opérations suivantes :  
  
1.  Crée un message XML qui représente un bon de commande.  
  
2.  Commence une activité BAMApiPo et ajoute à l'activité des informations relatives au bon de commande et au moment de sa réception.  
  
3.  Approuve ou rejette arbitrairement le bon de commande.  
  
4.  Met à jour l'activité BAMApiPo pour enregistrer l'état du bon de commande (accepté ou rejeté).  
  
5.  Si le bon de commande a été acceptée, la **RunOnce** méthode effectue également les opérations suivantes :  
  
    1.  Crée un message XML pour représenter un paquet à expédier et ajoute le message à la file d'attente des expéditions.  
  
    2.  Ajoute le message XML qui représente le bon de commande à la file d'attente des bons de commande à inclure dans une facture.  
  
    3.  Active la continuation de l'activité BAMApiPo.  
  
    4.  Met fin à l'activité BAMApiPo.  
  
 Le **RunOnce** méthode de la **ShipmentApplication** classe effectue les opérations suivantes :  
  
1.  Extrait de sa file d'attente un message XML qui représente un paquet à expédier.  
  
2.  Met à jour l'activité BAMApiPo pour enregistrer l'heure à laquelle le paquet a été expédié.  
  
3.  Met fin à l'activité BAMApiPo.  
  
 Le **RunOnce** méthode de la **InvoiceApplication** classe effectue les opérations suivantes :  
  
1.  Extrait de sa file d'attente un message XML qui représente un bon de commande à facturer.  
  
2.  Commence une activité BAMApiInvoice.  
  
3.  Crée une relation BAM entre l'activité BAMApiInvoice et l'activité BAMApiPo pour le bon de commande en cours de facturation.  
  
4.  Ajoute à l'activité BAMApiPo des informations relatives à la facture et à l'heure à laquelle elle a été créée.  
  
5.  Après un délai arbitraire pour simuler l'attente de la facture à payer, ajoute à l'activité BAMApiInvoice l'heure à laquelle la facture a été payée.  
  
6.  Met fin à l'activité BAMApiInvoice.  
  
 Le **principal** méthode de la **MainApp** classe initialise l’application. Elle effectue les opérations suivantes :  
  
1.  Crée un **DirectEventStream** objet.  
  
2.  Démarre plusieurs threads et appelle le **exécuter** méthode de la **POApplication** objet dans chaque thread.  
  
3.  Démarre plusieurs threads et appelle le **exécuter** méthode de la **ShipmentApplication** objet dans chaque thread.  
  
4.  Démarre plusieurs threads et appelle le **exécuter** méthode de la **InvoiceApplication** objet dans chaque thread.  
  
 Le **Global** classe définit des constantes qui sont utilisées par l’exemple d’application, telles que le nombre de threads pour créer et le pourcentage de bons de commande à rejeter.  
  
 Outre la solution [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], l'exemple contient également un fichier Microsoft [!INCLUDE[btsExcel](../includes/btsexcel-md.md)] qui définit les activités.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 Vous pouvez trouver cet exemple à  *\<exemples de chemin >*\BAM\BamApiSample.  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier| Description|  
|----------|-----------------|  
|BamApiSample.cs|Application instrumentée.|  
|BamApiSample.csproj|Projet de l'application instrumentée.|  
|BamApiSample.sln|Solution de l'application instrumentée.|  
|BamApiSample.xls|Feuille de style de définition BAM.|  
|Cleanup.bat|Fichier de commandes pour supprimer les exemples de fichiers déployés.|  
|Input.txt|Exemple d'entrée de configuration de l'intercepteur.|  
|InterceptorConfig.cs|Code de configuration de l'intercepteur pour l'exemple d'API.|  
|InterceptorConfig.csproj|Projet de configuration de l'intercepteur.|  
|Invoice_config.xml|Configuration de l'intercepteur de facture.|  
|Invoice_interceptor.bin|Intercepteur de facture sérialisé.|  
|PurchaseOrder_config.xml|Configuration de l'intercepteur de PurchaseOrder.|  
|PurchaseOrder_interceptor.bin|Intercepteur de PurchaseOrder sérialisé.|  
|Setup.bat|Fichier de commandes pour déployer et inscrire les exemples de fichiers.|  
|Shipment_config.xml|Configuration de l'intercepteur d'expédition.|  
|Shipment_interceptor.bin|Intercepteur d'expédition sérialisé.|  
  
## <a name="how-to-use-this-sample"></a>L’utilisation de cet exemple  
 Utilisez la procédure suivante pour exécuter l'exemple API BAM et afficher les résultats.  
  
#### <a name="to-run-the-bam-api-sample"></a>Pour exécuter l'exemple API BAM  
  
1.  Ouvrez une invite de commandes et exécutez  *\<exemples de chemin >*\BAM\ BamApiSample\setup.bat. Si vous utilisez [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], ouvrez l'invite de commandes en tant qu'administrateur.  
  
2.  Démarrer [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], puis ouvrez le  *\<exemples de chemin >*solution \BAM\ BamApiSample\BamApiSample.sln. Si vous utilisez [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], démarrez [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] en tant qu'administrateur.  
  
    > [!IMPORTANT]
    >  La ligne `//#define Interceptor` dans le fichier BamApiSample.cs doit être commentée. Ne supprimez pas le « // » de cette ligne. L'exemple API BAM utilise uniquement le code ne se trouvant pas à l'intérieur d'une directive de préprocesseur `#if Interceptor`.  
  
3.  Générez la solution.  
  
4.  Exécutez  *\<exemples de chemin d’accès >*\BAM\BamApiSample\bin\debug\BamApiSample.exe.  
  
     Le résultat ressemble à ceci :  
  
    ```  
    ...  
    New Purchase Order #17 Received  
    8 was shipped as pkg#87  
    New Purchase Order #18 Received.  
    Shipping package pkg#87 via DHL  
    13 was Approved.  
    18 was Rejected.  
    17 was Rejected.  
    11 was shipped as pkg#114  
    16 wsas Rejected.  
    Shipping package pkg#114 via DHL  
    Invoice #5 send for {2 5 1 9 4 8 11 }  
    Package pkg#49 was delivered  
    New Purchase Order #19 Received.  
    ...  
    ```  
  
5.  Après une minute environ, appuyez sur CTRL+C ou fermez la fenêtre de l'invite de commandes pour arrêter le programme BamApiSample.  
  
#### <a name="to-view-the-results-of-running-the-bam-api-sample"></a>Pour afficher les résultats de l'exécution de l'exemple API BAM  
  
1.  Ouvrez SQL Server Management Studio.  
  
2.  Dans SQL Server Management Studio, développez le serveur, **bases de données**, développez **BAMPrimaryImport**, puis développez **Tables**.  
  
3.  Avec le bouton droit **dbo.bam_BAMApiInvoice_Active** puis cliquez sur **ouvrir la Table**. Si vous utilisez [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], cliquez sur **sélectionner les 1000 lignes**.  
  
     Le contenu de la table bam_BAMApiInvoice_Active s'affiche dans le volet droit. Chaque ligne de la table représente une activité BAMApiInvoice démarrée mais non terminée.  
  
4.  Avec le bouton droit **dbo.bam_BAMApiPo_Completed** puis cliquez sur **ouvrir la Table**. Si vous utilisez [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], cliquez sur **sélectionner les 1000 lignes**.  
  
     Le contenu de la table bam_BAMApiPo_Completed s'affiche dans le volet droit. Chaque ligne de la table représente une activité BAMApiPo terminée.