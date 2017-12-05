---
title: "Étape 1 : Créer le Message de demande pour UPDATE_EMPLOYEE procédure stockée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4dd975d9-4b38-46e0-a926-4b325b0d7b5e
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e30225b79b14ffc237798ddde6f3fe40fb4aea9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-1-create-the-request-message-for-updateemployee-stored-procedure"></a>Étape 1 : Créer le Message de demande pour UPDATE_EMPLOYEE procédure stockée
![Étape 1 sur 2](../../adapters-and-accelerators/adapter-sql/media/step-1of2.gif "Step_1of2")  
  
 **Durée :** 10 minutes  
  
 **Objectif :** dans cette étape, vous ajoutez un projet de bibliothèque de classes c# à votre solution. Cette bibliothèque crée un message de demande de mémoire pour le **UPDATE_EMPLOYEE** procédure stockée. Dans les étapes ultérieures, l’orchestration envoie ce message à SQL Server pour exécuter la procédure stockée.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez avoir terminé les étapes de [leçon 2 : recevoir des Notifications de filtre et](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md).  
  
### <a name="to-create-a-request-message-for-updateemployee-stored-procedure"></a>Pour créer un message de demande pour UPDATE_EMPLOYEE procédure stockée  
  
1.  Ajouter un projet de bibliothèque de classes Visual c# à votre solution. Pour le nom du projet, tapez `UpdateEmployeeMessageCreator`.  
  
2.  Renommer **Class1.cs** à **UpdateEmployeeMessageCreator.cs**.  
  
3.  Copiez le code suivant dans le fichier .cs :  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Xml;  
    using System.IO;  
  
    namespace UpdateEmployeeMessageCreator  
    {  
        public class UpdateEmployeeMessageCreator  
        {  
            private static XmlDocument Message;  
            private static string XmlFileLocation;  
            private static string ResponseDoc;  
  
            public static XmlDocument XMLMessageCreator()  
            {  
                XmlFileLocation = "C:\\TestLocation\\CreateEmployeeMessage";  
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
  
     Cet extrait de code attend un message de demande pour le **UPDATE_EMPLOYEE** une procédure stockée à être présentes au C:\TestLocation\CreateEmployeeMessage. Le code utilise le message de demande pour créer un message de demande similaire au moment de l’exécution.  
  
4.  Ajouter un fichier de clé de nom fort au projet. Consultez [conditions préalables requises pour créer des applications SQL à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/prerequisites-to-create-sql-applications-using-the-sql-adapter.md).  
  
    1.  Dans l’Explorateur de solutions, cliquez sur le **UpdateEmployeeMessageCreator** de projet, puis cliquez sur **propriétés**.  
  
    2.  Dans le **propriété** fenêtre, cliquez sur **signature**.  
  
    3.  Dans le **signature** onglet, sélectionnez le **signer l’assembly** case à cocher.  
  
    4.  À partir de la **choisir un fichier de clé de nom fort** , cliquez sur  **\<Parcourir\>**.  
  
    5.  Accédez au dossier où vous avez créé le fichier de clé de nom fort, puis cliquez sur **ouvrir**.  
  
    6.  Cliquez sur **enregistrer** sur la barre de menus Standard. Fermer le **propriété** fenêtre.  
  
5.  créer le projet ; Cliquez sur le projet, puis cliquez sur **Build**.  
  
6.  Ajoutez une référence de projet au projet BizTalk dans la solution.  
  
    1.  Dans l’Explorateur de solutions, développez le projet BizTalk, cliquez sur **références**, puis cliquez sur **ajouter une référence**.  
  
    2.  Dans le **ajouter une référence** boîte de dialogue, cliquez sur le **projets** onglet.  
  
    3.  Dans la liste des noms de projet, sélectionnez **UpdateEmployeeMessageCreator**, cliquez sur **ajouter**, puis cliquez sur **OK**.  
  
7.  Création du projet crée la DLL d’assembly dans le dossier \bin\Debug du projet. Vous devez ajouter cette DLL pour le Global Assembly Cache (GAC).  
  
    1.  Démarrez une invite de commandes Visual Studio.  
  
    2.  À partir de l’invite de commandes, accédez au dossier \bin\Debug\ de la **UpdateEmployeeMessageCreator** projet.  
  
    3.  Sur l’invite de commandes, exécutez la commande suivante :  
  
        ```  
        gacutil /i UpdateEmployeeMessageCreator.dll  
        ```  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Dans cette étape, vous avez ajouté un projet de bibliothèque de classes UpdateEmployeeMessageCreator qui crée un message de demande au moment de l’exécution. Vous ajouté la référence à ce projet dans le projet BizTalk et également ajouter la DLL d’assembly dans le GAC.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Envoyer le message de demande à SQL Server et de recevoir la réponse, comme décrit dans [étape 2 : envoyer le Message de demande à SQL Server et de recevoir une réponse](../../adapters-and-accelerators/adapter-sql/step-2-send-the-request-message-to-sql-server-and-receive-response.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Leçon 3 : Exécuter une procédure stockée pour sélectionner les nouveaux employés ajoutés](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md)