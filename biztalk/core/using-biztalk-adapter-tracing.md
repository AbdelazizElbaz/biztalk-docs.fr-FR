---
title: "À l’aide du suivi des adaptateurs BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Adapter Trace Utility, installing
- installing, Adapter Trace Utility
- Adapter Trace Utility, enabling
- Adapter Trace Utility, running
- enabling, Adapter Trace Utility
ms.assetid: ddc6b2c7-9dee-43c1-950b-8fd580bfcb26
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1e14234363ace4b953fa4766a97502753572e6f
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="using-biztalk-adapter-tracing"></a>Utilisation du suivi des adaptateurs BizTalk
Cette rubrique décrit la procédure d'installation de l'outil Trace Log (Journal de suivi) et d'activation du suivi des adaptateurs BizTalk.  
  
## <a name="install-the-trace-log-tool"></a>Installation de l'outil Trace Log  
  
#### <a name="to-install-the-trace-log-tool-tracelogexe"></a>Pour installer l'outil de journal de suivi (tracelog.exe)  
  
1.  Téléchargez l'outil Trace Log sur le site Web [Microsoft® Windows® Software Development Kit Update for Windows Vista](http://go.microsoft.com/fwlink/?LinkId=128279) (en anglais).  
  
    > [!NOTE]
    >  Installez cette version (6.0) du Kit de développement logiciel même si vous exécutez [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]. Si vous installez le **Kit de développement logiciel Windows pour Windows Server 2008 et .NET Framework 3.5** version (v. 6.1), l’outil Trace Log n’est pas installé.  
  
2.  Lancez le programme d'installation Web de la **mise à jour du Kit de développement logiciel Microsoft® Windows® pour Windows Vista** en cliquant, au bas de la page Web, sur le lien correspondant au fichier **PSDK-x86.exe** .  
  
    > [!NOTE]
    >  Si vous utilisez une version 64 bits de Windows, téléchargez les fichiers adaptés à votre système.  
  
3.  Dans la boîte de dialogue **Sélectionner un type d'installation** , choisissez l'installation **personnalisée** , puis cliquez sur **Suivant**.  
  
4.  Acceptez l'emplacement d'installation par défaut, puis cliquez sur **Suivant**.  
  
5.  Dans la boîte de dialogue **Installation personnalisée** , désactivez toutes les cases à cocher relatives aux composants disponibles.  
  
6.  Développez le composant de **kit de développement SDK principal Microsoft Windows** , puis le composant **Outils** .  
  
7.  Choisissez le composant **Outils (Intel 64 bits)** et cliquez sur **Installation sur le disque dur local**.  
  
8.  Cliquez sur **Suivant**, puis de nouveau sur **Suivant** pour démarrer l'installation.  
  
    > [!NOTE]
    >  Après l'installation de la **mise à jour du Kit de développement logiciel Microsoft® Windows® pour Windows Vista** , vous pouvez être invité à redémarrer selon les fonctionnalités que vous avez choisi d'installer en plus de l'outil Trace Log. En effet, certains composants de la **mise à jour du Kit de développement logiciel Microsoft® Windows® pour Windows Vista** ne fonctionneront pas correctement sans un redémarrage. Vous pouvez utiliser l'outil Trace Log sans redémarrer.  
  
## <a name="enable-biztalk-adapter-tracing-with-tracecmd"></a>Activation du suivi des adaptateurs BizTalk avec trace.cmd  
  
#### <a name="to-enable-biztalk-adapter-tracing"></a>Pour activer le suivi des adaptateurs BizTalk  
  
1.  À l’invite de commandes, accédez au répertoire en cours le répertoire d’installation de BizTalk Server. Par défaut, BizTalk Server est installé dans le [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)] active.  Si vous utilisez une version 64 bits de Windows et BizTalk Server, le chemin d’installation est [!INCLUDE[btsBizTalkServerPathx64](../includes/btsbiztalkserverpathx64-md.md)].  
  
2.  Tapez la commande suivante et appuyez sur ENTRÉE :  
  
     **trace - tools « Chemin d’accès de l’outil Trace Log »**  
  
     Par défaut, l'outil Trace Log (tracelog.exe) se trouve dans le répertoire **C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin** . Si vous utilisez une version 64 bits de Windows, il se trouve dans le répertoire **C:\Program Files (x86)\Microsoft SDKs\Windows\v6.0\Bin**.  Vous devez indiquer le chemin d'accès à cet outil entre guillemets.  
  
     Par exemple, tapez la commande suivante et appuyez sur ENTRÉE :  
  
     **trace - tools « C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin »**  
  
    > [!NOTE]
    >  Le commutateur **-tools** indique au fichier Trace.cmd l'emplacement du fichier Tracelog.exe.  
    >   
    >  Si la commande fonctionne, la sortie doit correspondre à ce qui suit :  
    >   
    >  **2.0 - gérer BizTalk 2006 version Bits le suivi de trace.**  
    >   
    >  **Paramètre TRACE_TOOL_SEARCH_PATH à « C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin »**  
  
## <a name="capture-trace-output-with-tracecmd"></a>Capture de la sortie de traçage avec trace.cmd  
  
#### <a name="to-capture-trace-output"></a>Pour capturer la sortie de traçage  
  
1.  À l’invite de commandes, accédez au répertoire en cours le répertoire d’installation de BizTalk Server.  
  
2.  Au niveau d'une invite de commande, tapez la commande ci-après, puis appuyez sur la touche ENTRÉE :  
  
     **trace - Démarrer**  
  
3.  Reproduisez le scénario dont vous voulez capturer la sortie de traçage.  
  
4.  Au niveau d'une invite de commande, tapez la commande ci-après, puis appuyez sur la touche ENTRÉE :  
  
     **trace - arrêter**  
  
5.  Après l’arrêt de la trace, un fichier binaire nommé **Btstrace.bin** est généré dans le dossier dans lequel [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé.  
  
6.  Envoyez le fichier **Btstrace.bin** pour analyse aux Services de support technique Microsoft.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide des adaptateurs](../core/using-adapters.md)   
 [Résolution des problèmes de l’adaptateur Windows SharePoint Services](../core/troubleshooting-the-windows-sharepoint-services-adapter.md)