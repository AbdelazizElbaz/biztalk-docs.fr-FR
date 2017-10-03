---
title: "Générer le WSDL avec le Kit de développement logiciel de l’adaptateur LOB WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f701d78d-b3ad-4f75-b814-e5b1f1319fb9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f1075bbe59e15e3eeabde6c1d5c954460d1cb570
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="generate-wsdl-with-the-wcf-lob-adapter-sdk"></a>Générer le WSDL avec le Kit de développement logiciel de l’adaptateur LOB WCF
Pendant le développement d’un adaptateur, ou lorsque les métadonnées retournées par les modifications du système LOB, il est souvent utile d’afficher le Web Services Description Language (WSDL) qui est retourné à partir de l’adaptateur pour vérifier que les métadonnées pour vos opérations sont générées correctement. Il existe plusieurs méthodes pour générer le WSDL. Cette rubrique fournit des informations sur l’utilisation de svcutil.exe et le contrôle de recherche de métadonnées Parcourir.  

  
## <a name="use-svcutilexe"></a>Utiliser svcutil.exe  
 SvcUtil.exe est un utilitaire de ligne de commande fourni avec le Kit de développement qui accepte une URL et des paramètres facultatifs et retourne le WSDL. Voici un exemple d’utilisation de svcutil.exe pour retourner le WSDL de l’adaptateur d’écho :  
  
 ```
 Svcutil.exe “echov2://lobhostname/lobapplication?enableAuthentication=False” /target:metadata
 ```
  
 Il enregistre les métadonnées en tant que Microsoft.Adapters.Samples.Echov2.wsdl. Si votre adaptateur possède de nombreuses opérations, vous pouvez choisir de retourner uniquement les opérations souhaitées à l’aide de ' op = NomOpération ' en tant que partie de l’URI. Voici un exemple d’utilisation de ce pour retourner uniquement les informations de EchoStrings :  
  
```  
SvcUtil.exe “echov2://lobhostname/lobapplication?enableAuthentication=False&op=Echo/EchoStrings” /target:metadata  
```  
  
## <a name="use-the-metadata-search-browse-control"></a>Utilisez le contrôle de navigation de recherche de métadonnées  
 Le contrôle de recherche de métadonnées Parcourir est un contrôle Windows qui est utilisé dans les Assistants inclus dans [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. Vous pouvez ajouter ce contrôle à un projet Windows Forms dans Visual Studio et l’utiliser pour sélectionner votre adaptateur, les opérations de votre choisies et puis générer le WSDL.  
  
1.  Ouvrir un [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] invite de commandes.  
  
2.  Sur le **fichier** menu, sélectionnez **nouveau**, puis cliquez sur **projet**.  
  
3.  Dans le **nouveau projet** boîte de dialogue, sélectionnez **Application Windows** de **modèles**. Entrez un nom de projet, puis cliquez sur **OK**.  
  
4.  Ouvrez le **boîte à outils**, développez **contrôles communs**, avec le bouton droit le **boîte à outils**, puis cliquez sur **choisir des éléments de**.  
  
5.  Dans le **choisir des éléments de boîte à outils** boîte de dialogue Rechercher **MetadataUserControl** sur la **composants .NET Framework** onglet, sélectionnez la case à cocher en regard de cet élément, puis cliquez sur  **OK**.  
  
6.  À partir de la boîte à outils, faites glisser le MetadataUserControl vers Form1. Vous devrez peut-être redimensionner le formulaire pour afficher l’ensemble du contrôle. Vous devez être en mesure d’exécuter le projet maintenant et vérifiez que le contrôle fonctionne, ce qui vous permet de sélectionner un adaptateur et les opérations.  
  
7.  Pour générer le WSDL à l’aide de ce contrôle, vous devez ajouter du code à votre formulaire pour appeler le **GetWsdl** méthode de ce contrôle. L’exemple suivant montre comment appeler **GetWsdl** et enregistrer les données dans le fichier :  
  
    ```csharp  
    private void button1_Click(object sender, EventArgs e)  
    {  
       ServiceDescription sd = mdUserControl.GetWsdl();  
       FileStream myFileStream = new FileStream(tbWsdlFileName.Text, FileMode.OpenOrCreate, FileAccess.Write);  
       StreamWriter myStreamWriter = new StreamWriter(myFileStream);  
       sd.Write(myStreamWriter);  
       myStreamWriter.Flush();  
       myStreamWriter.Close();  
       MessageBox.Show("WSDL file " + tbWsdlFileName.Text + " is created.");  
    }  
  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Résoudre les problèmes d’adaptateur créé à l’aide de WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/troubleshoot-adapter-created-using-the-wcf-lob-adapter-sdk.md)