---
title: "Étape 4 : Création du projet de HeaderHelper | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects, helper projects
- private process tutorial, creating helper projects
ms.assetid: 82413537-032a-4368-8d77-d024a7c83b0b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2525e0e87106e2eeb82fb05b52b3ec69d4be876d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-4-creating-the-headerhelper-project"></a>Étape 4 : Création du projet de HeaderHelper
Dans cette étape, vous allez créer une [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] bibliothèque de classes. Lorsqu’une orchestration de processus privé reçoit un message entrant, la bibliothèque HeaderHelper détermine si la conversion d’un document est requise et si elle est nécessaire, effectue cette conversion. Cela permet à l’orchestration de travailler avec différentes versions des documents de Framework RNIF (RosettaNet Implementation). En outre, lorsqu’un message de réponse 3A2 est envoyé, la bibliothèque HeaderHelper effectue une conversion de documents supplémentaires avant de transmettre le message.  
  
### <a name="to-create-the-headerhelper-project"></a>Pour créer le projet HeaderHelper  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans l’Explorateur de solutions, cliquez sur la solution Contoso, pointez sur **ajouter**, puis cliquez sur **nouveau projet**.  
  
2.  Dans la boîte de dialogue Ajouter un nouveau projet, dans le volet Types de projets, sélectionnez **Visual C#**.  
  
3.  Dans le volet Modèles, sélectionnez le **bibliothèque de classes** modèle.  
  
4.  Dans le **nom** , tapez **HeaderHelper**, puis cliquez sur **OK** pour créer le projet.  
  
5.  Dans l’Explorateur de solutions, avec le bouton droit sur le **Class1.cs** de fichiers dans le **HeaderHelper** de projet, cliquez sur **renommer**, type **HeaderHelper.cs**, puis appuyez sur **entrée**.  
  
### <a name="to-create-the-helper-class"></a>Pour créer la classe d’assistance  
  
1.  Dans l’Explorateur de solutions, développez le **HeaderHelper** de projet, puis double-cliquez sur le **HeaderHelper.cs** nœud pour ouvrir le fichier source HeaderHelper.  
  
2.  Tapez le code suivant dans le fichier source, en remplaçant tout le code existant :  
  
    ```  
    using System;  
    using System.Xml;  
  
    namespace ContosoPriceAndAvailability  
    {  
        public class Helper  
        {  
            static public XmlDocument NormalizeHeader( XmlDocument curPip )  
            {  
                string strInput = curPip.OuterXml;  
                try  
                {  
                    XmlDocument xDoc = new XmlDocument();  
  
                    strInput = strInput.Replace("<!DOCTYPE Pip3A2PriceAndAvailabilityQuery SYSTEM \"3A2PriceAndAvailabilityQueryMessageGuideline_v1_3.dtd\"[]>",String.Empty);  
                    strInput = strInput.Replace("<Pip3A2PriceAndAvailabilityQuery>","<Pip3A2PriceAndAvailabilityQuery xmlns=\"http://schemas.microsoft.com/biztalk/btarn/2004/3A2PriceAndAvailabilityQueryMessageGuideline_v1_3.dtd\">");  
                    strInput = strInput.Replace("xml:",String.Empty);  
                    strInput = strInput.Replace("b:",String.Empty);  
                    strInput = strInput.Replace("lang:",String.Empty);  
                    strInput = strInput.Replace("ns1:",String.Empty);  
  
                    xDoc.LoadXml(strInput);  
  
                    return xDoc;  
                }  
                catch(Exception ex)  
                {  
                    System.Diagnostics.Debug.Write( ex.Message );  
                    throw ex;  
                }  
            }  
  
            static public string ReturnSCWithDocType( XmlDocument xmlDoc )  
            {  
                try  
                {  
                    string sResponse = xmlDoc.InnerXml;  
                    sResponse=sResponse.Replace("ns0:",String.Empty);  
                    xmlDoc.LoadXml(sResponse);  
                    xmlDoc.DocumentElement.RemoveAllAttributes();  
                    sResponse = xmlDoc.InnerXml;  
  
                    sResponse = sResponse.Insert(0,"<!DOCTYPE Pip3A2PriceAndAvailabilityResponse SYSTEM \"3A2PriceAndAvailabilityResponseMessageGuideline_v1_3.dtd\">");  
                    sResponse = sResponse.Replace("ns0:",String.Empty);  
                    sResponse = sResponse.Replace("b:",String.Empty);  
                    sResponse = sResponse.Replace("lang:",String.Empty);  
                    sResponse = sResponse.Replace("ns1:",String.Empty);  
  
                    return sResponse;  
                }  
                catch(Exception ex)  
                {  
                    throw ex;  
                }  
            }  
        }  
    }  
    ```  
  
3.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
### <a name="to-create-a-strong-named-assembly-for-the-headerhelper-project"></a>Pour créer un assembly à nom fort pour le projet HeaderHelper  
  
1.  Dans l’Explorateur de solutions, cliquez sur le **HeaderHelper** de projet, puis cliquez sur **propriétés**.  
  
2.  Dans la boîte de dialogue Pages de propriétés HeaderHelper, sélectionnez **signature** dans le volet gauche du volet Propriétés HeaderHelp.  
  
3.  Dans le volet droit, cliquez sur **signer l’Assembly**.  
  
4.  Cliquez sur le **choisir un fichier de clé de nom fort** zone de texte, puis sélectionnez  **\<Parcourir\>**  dans la liste déroulante.  
  
5.  Dans la boîte de dialogue Sélectionner le fichier, accédez à l’emplacement de votre assembly de Contoso, double-cliquez sur **FabConPriceAvail.snk**.  
  
6.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
7.  Dans l’Explorateur de solutions, développez le **HeaderHelper** de projet, développez le **propriétés** nœud, puis double-cliquez sur le **AssemblyInfo.cs** nœud ouvrir AssemblyInfo.cs fichier source.  
  
8.  Dans le fichier AssemblyInfo.cs source, tapez le code suivant sur la ligne après l’attribut AssemblyCulture :  
  
    ```  
    [assembly: AssemblyKeyFile("../../../FabConPriceAvail.snk")]  
    ```  
  
9. Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
### <a name="to-build-and-deploy-the-headerhelper-project"></a>Pour générer et déployer le projet HeaderHelper  
  
1.  Dans l’Explorateur de solutions, cliquez sur le **HeaderHelper** de projet, puis cliquez sur **Build**.  
  
2.  Démarrez une **invite de commandes Visual Studio 2012**.  
  
3.  À l’invite de commandes, accédez à l’emplacement de la **HeaderHelper** le répertoire de sortie de projet (le dossier \Bin\Debug).  
  
4.  À l’invite de commandes, tapez **gacutil /if HeaderHelper.dll** et appuyez sur **entrée** pour installer le **HeaderHelper** assembly dans le **Global Assembly Cache** .  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 5 : Modification de l’orchestration du processus privé de Contoso](../../adapters-and-accelerators/accelerator-rosettanet/step-5-modifying-the-contoso-private-process-orchestration.md)