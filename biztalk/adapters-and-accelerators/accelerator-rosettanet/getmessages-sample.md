---
title: Exemple de GetMessages | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29e575fa-d68b-4975-84b8-da4f17bd2db3
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f2ebc4ce5b87a0b698f0295fdf29c8f7138efed7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="getmessages-sample"></a>Exemple de GetMessages
Cette rubrique fournit des exemples de code que vous pouvez utiliser pour récupérer des messages à partir d’une des tables de non répudiation de message ou une des tables de métier (LOB) dans un format lisible. Les tables de non répudiation de message incluent MessageStorageIn et MessageStorageOut de la [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]base de données Archive ; les tables LOB incluent MessageFromLOB et MessageToLOB dans les [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]base de données.  
  
 Utilisez `GetMessages` pour le dépannage ou développement. Par défaut, le code retourne une chaîne en base 64.  
  
> [!NOTE]
>  L’exemple de code GetMessages.cs contient deux sections de code : un pour la récupération des messages à partir d’une des tables LOB et un pour la récupération des messages à partir d’une des tables de non répudiation. Créer des applications distinctes pour chaque objectif.  
  
### <a name="to-retrieve-messages-from-an-lob-table"></a>Pour récupérer des messages à partir d’une table LOB  
  
1.  Ajoutez le code suivant à votre programme :  
  
     `private static string GetLOBMessage(string sMessageSource, string sMessageID)`  
  
2.  Définir le `sMessageSource` paramètre à la table MessagesToLOB ou MessagesFromLOB.  
  
3.  Définir le `sMessageID` paramètre à la valeur de la **MessageID** champ dans la base de données.  
  
    > [!NOTE]
    >  L’application retourne une chaîne qui contient le message récupéré.  
  
### <a name="to-retrieve-messages-from-a-non-repudiation-table"></a>Pour récupérer des messages à partir d’une table de non répudiation  
  
1.  Ajoutez le code suivant à votre programme :  
  
     `private static string GetNRMessage(string sMessageSource, string sMessageID)`  
  
2.  Définir le `sMessageSource` paramètre soit la table MessageStorageIn ou MessageStorageOut.  
  
3.  Définir le `sMessageID` paramètre à la valeur de la **RecordID** champ dans la base de données.  
  
    > [!NOTE]
    >  L’application retourne une chaîne qui contient le message récupéré.  
  
## <a name="demonstrates"></a>Montre  
 L’exemple de GetMessages inclut les deux sections de code suivantes :  
  
-   Une section vous montre comment récupérer un message binaire à partir d’une des tables non répudiation et le convertir en format ASCII lisible.  
  
-   L’autre section vous montre comment récupérer un message à partir d’une des tables LOB. Un message dans une table LOB étant déjà sous forme de ASCII, il s’agit d’une instruction SQL select.  
  
    > [!IMPORTANT]
    >  À des fins de démonstration, l’exemple de code fourni utilise une instruction SQL directe qui est sujette aux vulnérabilités d’injection SQL. Dans un environnement de production, il est recommandé d’utiliser des procédures stockées SQL paramétrées, plutôt que l’instruction SQL directe, pour empêcher ces vulnérabilités.  
  
## <a name="example"></a>Exemple  
 Utilisez une des deux sections dans l’exemple de code suivant pour la récupération des messages à partir d’une des tables non répudiation ou une des tables LOB.  
  
```  
using System;  
using System.Text;  
using System.Data.SqlClient;   
using Microsoft.Solutions.BTARN.Shared;  
  
namespace Microsoft.Solutions.BTARN.Admin  
{  
  
      /// <summary>  
      /// Summary description for GetMessages.  
      /// </summary>  
      class GetMessages  
      {  
            /// <summary>  
            /// The main entry point for the application.  
            /// </summary>  
            [STAThread]  
            static void Main(string[] args)  
            {  
                  Console.WriteLine(GetLOBMessage("MessagesFromLOB", "bce5b580daf543a990a4f37331f31e42"));  
                  Console.WriteLine(GetLOBMessage("MessagesToLOB", "bce5b580daf543a990a4f37331f31e42"));  
                  Console.WriteLine(GetNRMessage("MessageStorageIn", "dc06e9cfecd746a889dd6ea7beb3ba21"));  
                  Console.WriteLine(GetNRMessage("MessageStorageOut", "dc06e9cfecd746a889dd6ea7beb3ba21"));  
            }  
  
            /// <summary>  
            /// Retrieve a message from the LOB tables in the BTARNDATA database  
            /// </summary>  
            /// <param name="sMessageSource">Can be either MessagesFromLOB or MessagesToLOB</param>  
            /// <param name="sMessageID">The value of the MessageID field in the database</param>  
            /// <returns>Returns a string that contains the retrieved message</returns>        
            private static string GetLOBMessage(string sMessageSource, string sMessageID)  
            {  
                  SqlDataReader localReader = null;  
                  SqlConnection sqlConnection = null;  
                  SqlCommand sqlCommand = null;  
                  string sReturnedMessage="";              
                  string sQuery;  
  
                  sqlConnection = new SqlConnection(RuntimeGlobal.DataDbConnectionString);  
                  sQuery = "SELECT ServiceContent from " + sMessageSource + " WHERE MessageID=N'" + sMessageID +"'";  
  
                  sqlCommand = new SqlCommand(sQuery, sqlConnection);  
                  sqlConnection.Open();  
  
                  localReader = sqlCommand.ExecuteReader();  
  
                  if (localReader.Read())  
                        sReturnedMessage=localReader.GetString(0);  
  
                  localReader.Close();  
                  sqlConnection.Close();        
                  return sReturnedMessage;              
            }  
  
            /// <summary>  
            /// Retrieve a message from the non-repudiation tables in the BTARNArchive database  
            /// </summary>  
            /// <param name="sMessageSource">Can be either MessageStorageIn or MessageStorageOut</param>  
            /// <param name="sMessageID">The value of the RecordID field in the database</param>  
            /// <returns>Returns a string that contains the retrieved message</returns>  
            private static string GetNRMessage(string sMessageSource, string sMessageID)  
            {  
                  SqlDataReader localReader = null;  
                  SqlConnection sqlConnection = null;  
                  SqlCommand sqlCommand = null;  
                  string sReturnedMessage="";              
                  string sQuery;  
  
                  sqlConnection = new SqlConnection(RuntimeGlobal.ArchiveDbConnectionString);  
                  sQuery = "SELECT Content from " + sMessageSource + " WHERE RecordID=N'" + sMessageID +"'";  
  
                  sqlCommand = new SqlCommand(sQuery, sqlConnection);  
                  sqlConnection.Open();  
  
                  localReader = sqlCommand.ExecuteReader();  
  
                  if (localReader.Read())  
                  {  
                        //Determine the size of the field in bytes and create a new byte array  
                        byte[] bData= new byte[localReader.GetBytes(0, 0, null, 0, 0)];  
  
                        //Read the value of the field into bData  
                        localReader.GetBytes(0, 0, bData, 0, bData.Length);  
  
                        //Convert the byte array into a string  
                        sReturnedMessage=Encoding.ASCII.GetString(bData);  
                  }  
  
                  localReader.Close();  
                  sqlConnection.Close();        
                  return sReturnedMessage;              
            }  
      }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de messagerie](../../adapters-and-accelerators/accelerator-rosettanet/messaging-samples.md)