---
title: "Appeler les BAPI dans SAP à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAPIs, invoking by using the WCF service model
- WCF service model, invoking BAPIs
ms.assetid: be3c48d6-2213-4ae5-97f4-634fbc423022
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 437c88516cfb771e0e5ae10807391235d602eb37
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-bapis-in-sap-using-the-wcf-service-model"></a>Appeler les BAPI dans SAP à l’aide du modèle de Service WCF
Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] met en évidence des interfaces BAPI en tant que :  
  
-   **Opérations RFC**. Interfaces BAPI comme n’importe quel autre RFC sont signalées sous le nœud RFC dans la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
-   **Méthodes des objets métiers SAP**. En tant que méthodes d’objets métier, les interfaces BAPI sont signalées par un objet métier sous le nœud BAPI dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
 Si vous appelez un BAPI sous la forme d’une opération de RFC ou une méthode d’objet métier, chaque BAPI fait toujours partie d’un LUW sur le système SAP.  
  
 Pour une vue d’ensemble de la façon dont [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge BAPI, consultez [opérations sur les BAPI dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md).  
  
 Lorsque vous utilisez le modèle de service WCF pour appeler des interfaces BAPI en tant que méthodes d’objet métier, chaque objet de métier SAP est représenté par une classe de client WCF et les interfaces BAPI de cet objet sont représentés en tant que méthodes sur le client. Vous pouvez utiliser la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer une classe de client WCF pour les objets métier spécifique qui contient des méthodes pour chaque BAPI que vous souhaitez appeler dans votre code. Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère également des types .NET pour encapsuler les paramètres et types de données qui sont utilisés par chaque BAPI. Vous pouvez ensuite créer une instance de cette classe de client WCF et appeler ses méthodes pour appeler la cible de BAPI.  
  
 Les sections suivantes vous montrent comment appeler des interfaces BAPI en tant que méthodes d’objets métier et expliquent comment les transactions BAPI sont prises en charge dans le modèle de service WCF.  
  
## <a name="the-wcf-client-class"></a>La classe de Client WCF  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] met en évidence un autre contrat de service, pour chaque objet de l’entreprise. Cela signifie que, pour chaque objet métier WCF unique classe de client est créée. Le nom de cette classe est basé sur le type d’objet métier. Par exemple pour l’objet métier Sales Order (type d’objet métier BUS2032), la classe de client WCF est **BapiBUS2032Client**. Chaque cible BAPI dans l’objet métier est représentée comme une méthode dans la classe de client WCF générée. Dans chaque méthode :  
  
-   Paramètres d’exportation SAP sont exposés en tant que **hors** paramètres  
  
-   Paramètres d’appel SAP sont exposés en tant que **ref** paramètres.  
  
-   Les types SAP complexes telles que les structures sont signalées en tant que classes .NET avec des propriétés qui correspondent aux champs de type SAP. Ces classes sont définies dans l’espace de noms suivant : microsoft.lobservices.sap._2007._03.Types.Rfc.  
  
 BAPI_TRANSACTION_COMMIT et BAPI_TRANSACTION_ROLLBACK sont signalées pour chaque objet de l’entreprise et vous devez toujours inclure ces éléments dans votre client WCF.  
  
 Le code suivant montre une partie d’une classe de client WCF générée pour l’objet d’entreprise de vente. Ce client contient des méthodes pour appeler CREATEFROMDAT2, BAPI_TRANSACTION_COMMIT et BAPI_TRANSACTION_ROLLBACK. Les constructeurs et tout autre code a été omis par souci de clarté.  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class BapiBUS2032Client : System.ServiceModel.ClientBase<BapiBUS2032>, BapiBUS2032 {  
  
    // Code has been removed for clarity  
  
    /// <summary>The Metadata for this RFC was generated using the RFC SDK.</summary>  
    /// <param name="SALESDOCUMENT">Number of Generated Document</param>  
    /// <param name="BEHAVE_WHEN_ERROR">Error Handling</param>  
    /// …  
    /// <param name="ORDER_TEXT">Texts</param>  
    /// <param name="PARTNERADDRESSES">BAPI Reference Structure for Addresses (Org./Company)</param>  
    /// <param name="RETURN">Return Messages</param>  
    /// <returns></returns>  
    public string CREATEFROMDAT2(  
                string BEHAVE_WHEN_ERROR,   
                string BINARY_RELATIONSHIPTYPE,   
                string CONVERT,   
                string INT_NUMBER_ASSIGNMENT,   
                microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISDLS LOGIC_SWITCH,   
                microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISDHD1 ORDER_HEADER_IN,   
                microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISDHD1X ORDER_HEADER_INX,   
                string SALESDOCUMENTIN,   
                microsoft.lobservices.sap._2007._03.Types.Rfc.BAPI_SENDER SENDER,   
                string TESTRUN,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPIPAREX[] EXTENSIONIN,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICCARD[] ORDER_CCARD,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICUBLB[] ORDER_CFGS_BLOB,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICUINS[] ORDER_CFGS_INST,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICUPRT[] ORDER_CFGS_PART_OF,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICUCFG[] ORDER_CFGS_REF,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICUREF[] ORDER_CFGS_REFINST,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICUVAL[] ORDER_CFGS_VALUE,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICUVK[] ORDER_CFGS_VK,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICOND[] ORDER_CONDITIONS_IN,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICONDX[] ORDER_CONDITIONS_INX,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISDITM[] ORDER_ITEMS_IN,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISDITMX[] ORDER_ITEMS_INX,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISDKEY[] ORDER_KEYS,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPIPARNR[] ORDER_PARTNERS,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISCHDL[] ORDER_SCHEDULES_IN,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISCHDLX[] ORDER_SCHEDULES_INX,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISDTEXT[] ORDER_TEXT,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPIADDR1[] PARTNERADDRESSES,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPIRET2[] RETURN) { ...}  
  
    /// <summary>The Metadata for this RFC was generated using the RFC SDK.</summary>  
    /// <param name="RETURN">Confirmations</param>  
    /// <param name="WAIT">Using the command `COMMIT AND WAIT`</param>  
    /// <returns></returns>  
    public microsoft.lobservices.sap._2007._03.Types.Rfc.BAPIRET2 BAPI_TRANSACTION_COMMIT(string WAIT) { ... }  
  
    /// <summary>The Metadata for this RFC was generated using the RFC SDK.</summary>  
    /// <param name="RETURN">Confirmations</param>  
    /// <returns></returns>  
    public microsoft.lobservices.sap._2007._03.Types.Rfc.BAPIRET2 BAPI_TRANSACTION_ROLLBACK() { ... }  
}  
```  
  
## <a name="bapi-transactions-in-the-wcf-service-model"></a>Transactions BAPI dans le modèle de Service WCF  
 Chaque BAPI, si elle est appelée en tant qu’une demande de changement ou une méthode d’objet métier, fait partie d’une transaction (LUW) sur le système SAP. et chaque BAPI reçu sur la même connexion SAP fait partie de la même transaction BAPI sur le système SAP. SAP valide ou annule la transaction BAPI lorsqu’il reçoit un BAPI_TRANSACTION_COMMIT ou un BAPI_TRANSACTION_ROLLBACK sur la connexion. Après qu’une validation ou restauration a été effectuée, BAPI suivant reçu sur la connexion commence une nouvelle transaction.  
  
 Pour la carte chaque canal WCF dispose d’une connexion SAP dédiée. Dans le modèle de service WCF, chaque client WCF a un canal interne qui est utilisé d’envoyer des messages au système SAP. Cela signifie que les interfaces BAPI qui sont appelées à l’aide d’un client WCF spécifique font partie d’une transaction BAPI unique sur le système SAP. Cela constitue une limitation importante lorsque vous utilisez le modèle de service WCF pour appeler des interfaces BAPI en tant que méthodes d’objet métier. Étant donné que chaque objet de métier SAP est représenté par une classe de client WCF dédiée, vous ne pouvez pas appeler BAPI à partir de deux objets différents dans le cadre de la même transaction. La contourner ce problème consiste à appeler les interfaces BAPI en tant qu’opérations de RFC. C’est parce que le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère un seul client WCF pour les opérations de RFC, et, par conséquent, toutes les opérations sont appelées à l’aide de ce client sont envoyées via le même canal WCF.  
  
> [!IMPORTANT]
>  Si vous souhaitez inclure des interfaces BAPI issues d’objets SAP différentes dans la même transaction BAPI, vous devez les appeler en tant qu’opérations RFC (à l’aide de ce même client WCF). Vous ne pouvez pas les appeler en tant que méthodes d’objet métier.  
  
 Vous appelez BAPI_TRANSACTION_COMMIT ou BAPI_TRANSACTION_ROLLBACK pour valider ou restaurer la transaction BAPI sur le système SAP. L’adaptateur met en évidence ces interfaces deux BAPI :  
  
-   Sous le nœud de base en tant qu’opérations de RFC.  
  
-   Sous chaque objet de l’entreprise.  
  
 Pour plus d’informations sur la façon dont l’adaptateur prend en charge les transactions BAPI sur SAP, consultez [opérations sur les BAPI dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md).  
  
## <a name="how-to-create-an-application-that-invokes-bapis-as-methods-of-business-objects"></a>Comment créer une Application qui appelle des interfaces BAPI en tant que méthodes d’objets métier  
 Cette section fournit des informations sur l’appel des interfaces BAPI en tant que méthodes d’objets métier. La même procédure doit être suivie pour appeler des interfaces BAPI en tant qu’opérations de RFC, à ceci près que vous créez un client WCF qui cible les BAPI en tant qu’opérations RFC et l’utiliser pour appeler chaque BAPI.  
  
 Pour créer une application cliente BAPI, procédez comme suit.  
  
#### <a name="to-create-an-bapi-client-application"></a>Pour créer une application cliente BAPI  
  
1.  Générer une classe de client WCF. Utilisez la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou ServiceModel Metadata Utility Tool (svcutil.exe) pour générer une classe de client WCF (ou classes) qui cible les objets et interfaces BAPI avec lequel vous souhaitez travailler. Veillez à inclure le BAPI_TRANSACTION_COMMIT et les méthodes BAPI_TRANSACTION_ROLLBACK (BAPI) exposées pour chaque objet d’entreprise cible. Pour plus d’informations sur la façon de générer un client WCF, consultez [génération d’un Client WCF ou un contrat de Service WCF pour les artefacts de Solution SAP](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).  
  
2.  Créez une instance de la classe de client WCF générée à l’étape 1 et créer et configurer un client WCF. Configuration du client WCF implique la spécification de la liaison et l’adresse de point de terminaison que le client utilisera. Ce faire, vous pouvez soit impérativement dans du code ou de façon déclarative dans la configuration. Pour plus d’informations sur la façon de spécifier une liaison de client, consultez [configurer une liaison de Client pour le système SAP](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md). Le code suivant initialise le client WCF pour l’objet métier SAP de vente (BUS2032) à partir de la configuration et définit les informations d’identification pour le système SAP.  
  
    ```  
    BapiBUS2032Client bapiClient = new BapiBUS2032Client("SAPBinding_BapiBUS2032");  
  
    bapiClient.ClientCredentials.UserName.UserName = "YourUserName";  
    bapiClient.ClientCredentials.UserName.Password = "YourPassword";  
    ```  
  
3.  Ouvrez le client WCF.  
  
    ```  
    bapiClient.Open();  
    ```  
  
4.  Appeler des méthodes sur le client WCF créé à l’étape 2 pour appeler les interfaces BAPI appropriés sur le système SAP. Vous pouvez appeler plusieurs interfaces BAPI sur le système SAP.  
  
5.  Terminer la transaction par :  
  
    1.  Appeler la méthode BAPI_TRANSACTION_COMMIT pour valider la transaction.  
  
        ```  
        bapiClient.BAPI_TRANSACTION_COMMIT("X");  
        ```  
  
    2.  Appeler la méthode BAPI_TRANSACTION_ROLLBACK pour restaurer la transaction.  
  
        ```  
        bapiClient.BAPI_TRANSACTION_ROLLBACK();  
        ```  
  
6.  Fermez le client WCF.  
  
    ```  
    bapiClient.Close();   
    ```  
  
### <a name="example"></a>Exemple  
 L’exemple suivant appelle BAPI CREATEFROMDAT2 sur l’objet métier Sales Order. Il appelle BAPI plusieurs fois et appelle ensuite BAPI_TRANSACTION_COMMIT pour valider la transaction. Si une erreur se produit lors de l’appel BAPI, BAPI_TRANSACTION_ROLLBACK est appelé dans le Gestionnaire d’exceptions pour annuler la transaction.  
  
 La méthode CREATEFROMDAT2 prend de paramètres ; ils sont omis dans l’exemple par souci de concision. Vous trouverez un exemple qui montre comment les transactions BAPI dans les exemples fournis avec Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemples pour l’adaptateur SAP ](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md).  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add WCF, Adapter LOB SDK, and SAP Adapter namepaces  
using System.ServiceModel;  
using Microsoft.Adapters.SAP;  
using Microsoft.ServiceModel.Channels;  
  
// Include this namespace for Adapter LOB SDK and SAP exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
using microsoft.lobservices.sap._2007._03.Types.Rfc;  
  
// This Example demonstrates BAPI transactions. Two sales orders are  
// created using the CREATEFROMDAT2 method of a SAP Business Object.   
// After the orders are created, the BAPI transaction is committed.   
// If an exception occurs when sending the BAPIs, the BAPI transaction is   
// rolled back.  
//   
  
namespace SapBapiTxClientSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Create the BAPI client from the generated endpoint configuration.  
  
            BapiBUS2032Client bapiClient = null;  
  
            Console.WriteLine("BAPI transaction sample started");  
            Console.WriteLine("\nCreating business object client");  
  
            try  
            {  
                bapiClient = new BapiBUS2032Client("SAPBinding_BapiBUS2032");  
  
                bapiClient.ClientCredentials.UserName.UserName = "YourUserName";  
                bapiClient.ClientCredentials.UserName.Password = "YourPassword";  
  
                // Open the BAPI Client  
                bapiClient.Open();  
  
                ...  
  
                // send first BAPI  
                try  
                {  
                    string salesDocNumber1 = bapiClient.CREATEFROMDAT2(  
                        ...  
                        // parameters ommitted  
                        ...                          
                        );  
                }  
                catch (Exception ex)  
                {  
                    bapiClient.BAPI_TRANSACTION_ROLLBACK();  
                    throw;  
                }  
  
                ...  
  
                // send second BAPI  
                try  
                {  
                    string salesDocNumber1 = bapiClient.CREATEFROMDAT2(  
                        ...  
                        // parameters omitted  
                        ...                          
                        );  
                }  
                catch (Exception ex)  
                {  
                    bapiClient.BAPI_TRANSACTION_ROLLBACK();  
                    throw;  
                }  
  
                ...  
  
                // Commit BAPI Transaction  
                try  
                {  
                    bapiClient.BAPI_TRANSACTION.Commit();  
                }  
                catch (Exception ex)  
                {  
                    bapiClient.BAPI_TRANSACTION_ROLLBACK();  
                    throw;  
                }  
  
                ...  
  
            }  
            catch (ConnectionException cex)  
            {  
                // Get here if problem connecting to the SAP system   
  
                Console.WriteLine("Exception occurred connecting to the SAP system");  
                Console.WriteLine(cex.InnerException.Message);  
            }  
            catch (TargetSystemException tex)  
            {  
                // Get here if the SAP system returns an exception  
  
                Console.WriteLine("Exception occurred on the SAP System");  
                Console.WriteLine(tex.InnerException.Message);  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                }  
            }  
            finally  
            {  
            // Close the client when finished  
                if (bapiClient != null)  
                {  
                    if (bapiClient.State == CommunicationState.Opened)  
                        bapiClient.Close();  
                    else  
                        bapiClient.Abort();  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)  
 [Opérations sur les BAPI dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md)