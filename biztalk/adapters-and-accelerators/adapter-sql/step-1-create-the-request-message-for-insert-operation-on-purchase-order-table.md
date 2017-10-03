---
title: "Étape 1 : Créer le Message de demande pour l’opération d’insertion sur la Table de Purchase_Order | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fde018d8-9d9a-42ea-8ee9-e3632450b9d7
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63d27a186cffc86a79f0a40f73cc6a0c1791c3b6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-create-the-request-message-for-insert-operation-on-purchaseorder-table"></a>Étape 1 : Créer le Message de demande pour l’opération d’insertion sur la Table de Purchase_Order
![Étape 1 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")  
  
 **Durée :** 10 minutes  
  
 **Objectif :** dans cette étape, vous ajoutez un projet de bibliothèque de classes c# à votre solution. Cette bibliothèque crée un message de demande de mémoire pour l’opération d’insertion sur la **Purchase_Order** table. Dans les étapes ultérieures, l’orchestration envoie ce message à SQL Server pour insérer des enregistrements dans la table.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez avoir terminé les étapes de [leçon 3 : exécuter une procédure stockée pour sélectionnez Nouveau employés ajouté](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md).  
  
### <a name="to-create-a-request-message-for-insert-operation"></a>Pour créer un message de demande pour l’opération d’insertion  
  
1.  Ajouter un projet de bibliothèque de classes Visual c# à votre solution. Pour le nom du projet, tapez `UpdatePOMessageCreator`.  
  
2.  Renommer **Class1.cs** à **UpdatePOMessageCreator.cs**.  
  
3.  Copiez le code suivant dans le fichier .cs :  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Xml;  
    using System.IO;  
  
    namespace UpdatePOMessageCreator  
    {  
        public class UpdatePOMessageCreator  
        {  
            private static XmlDocument Message;  
            private static string XmlFileLocation;  
            private static string ResponseDoc;  
  
            public static XmlDocument XMLMessageCreator()  
            {  
                XmlFileLocation = "C:\\TestLocation\\CreatePOMessage";  
                try  
                {  
                    ResponseDoc = (Directory.GetFiles(XmlFileLocation, "*.xml", SearchOption.TopDirectoryOnly))[0];  
                }  
                catch (Exception ex)  
                {  
                    Console.WriteLine("Trying to get XML from: " + XmlFileLocation);  
                    Console.WriteLine("EXCEPTION: " + ex.ToString());  
                    throw ex;  
                }  
  
                //Create Message From XML  
                Message = new XmlDocument();  
  
                Message.PreserveWhitespace = true;  
  
                Message.Load(ResponseDoc);  
  
                return Message;  
            }  
        }  
    }  
  
    ```  
  
     Cet extrait de code attend un message de demande pour l’opération d’insertion sur la **Purchase_Order** table se trouver devant C:\TestLocation\CreatePOMessage. Le code utilise le message de demande pour créer un message de demande similaire au moment de l’exécution.  
  
4.  Ajouter un fichier de clé de nom fort au projet. Pour obtenir des instructions sur la création d’un fichier de clé de nom fort, consultez [conditions préalables requises pour créer des applications SQL à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/prerequisites-to-create-sql-applications-using-the-sql-adapter.md).  
  
    1.  Dans l’Explorateur de solutions, cliquez sur le **UpdatePOMessageCreator** projet puis cliquez sur **propriétés**.  
  
    2.  Dans le **propriété** fenêtre, cliquez sur **signature**.  
  
    3.  Dans le **signature** onglet, sélectionnez le **signer l’assembly** case à cocher.  
  
    4.  À partir de la **choisir un fichier de clé de nom fort** , cliquez sur  **\<Parcourir >**.  
  
    5.  Accédez au dossier où vous avez créé le fichier de clé de nom fort, puis cliquez sur **ouvrir**.  
  
    6.  Cliquez sur **enregistrer** sur la **Standard** barre de menus. Fermer le **propriété** fenêtre.  
  
5.  créer le projet ; Cliquez sur le projet, puis cliquez sur **Build**.  
  
6.  Ajoutez une référence de projet au projet BizTalk dans la solution.  
  
    1.  Dans l’Explorateur de solutions, développez le projet BizTalk, cliquez sur **références**, puis cliquez sur **ajouter une référence**.  
  
    2.  Dans le **ajouter une référence** boîte de dialogue, cliquez sur le **projets** onglet.  
  
    3.  Dans la liste des noms de projet, sélectionnez **UpdatePOMessageCreator**, cliquez sur **ajouter**, puis cliquez sur **OK**.  
  
7.  Création du projet crée la DLL d’assembly dans le dossier \bin\Debug du projet. Vous devez ajouter cette DLL pour le Global Assembly Cache (GAC).  
  
    1.  Démarrez une invite de commandes Visual Studio.  
  
    2.  À partir de l’invite de commandes, accédez au dossier \bin\Debug\ de la **UpdatePOMessageCreator** projet.  
  
    3.  Sur l’invite de commandes, exécutez la commande suivante :  
  
        ```  
        gacutil /i UpdatePOMessageCreator.dll  
        ```  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Dans cette étape, vous avez ajouté un projet de bibliothèque de classes UpdatePOMessageCreator qui crée un message de demande au moment de l’exécution. Vous ajouté la référence à ce projet dans le projet BizTalk et également ajouter la DLL d’assembly dans le GAC.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous mappez le message de réponse pour la procédure stockée de UPDATE_EMPLOYEE au message de demande pour l’opération d’insertion sur **Purchaser_Order** table.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 2 : Mapper le Message de réponse UPDATE_EMPLOYEE insérer le Message de demande d’opération](../../adapters-and-accelerators/adapter-sql/step-2-map-update_employee-response-to-insert-operation-request.md)   
 [Leçon 4 : Effectuer une opération d’insertion sur la Table de commande d’achat](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)