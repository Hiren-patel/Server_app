Server_app
==========<%@ Page Title="Server Submission" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Default.aspx.cs" Inherits="WebApplication1._Default" %>

<asp:Content runat="server" ID="FeaturedContent" ContentPlaceHolderID="FeaturedContent">
    <section class="featured">
        <div class="content-wrapper">
            <hgroup class="title">
                <h1><%:Title %>.</h1>

            </hgroup>
           
        </div>

    </section>


</asp:Content>
<!-- Contains the data entry boxes on the main form -->
<asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">
   <div class="test" >
                Server Name: 
                <asp:TextBox id="servername" runat="server" />
                <br /><br />
       
                 IP Address: 
                <asp:TextBox id="ipaddress" runat="server"/>
                <asp:RegularExpressionValidator ID="RegularExpressionValidator2" runat="server"  ErrorMessage="Please Check your IP address!" ControlToValidate="ipaddress" ValidationExpression="^(\d|[1-9]\d|1\d\d|2([0-4]\d|5[0-5]))\.(\d|[1-9]\d|1\d\d|2([0-4]\d|5[0-5]))\.(\d|[1-9]\d|1\d\d|2([0-4]\d|5[0-5]))\.(\d|[1-9]\d|1\d\d|2([0-4]\d|5[0-5]))$"></asp:RegularExpressionValidator>
                <br /><br /> 
          
                Disk Sizes:
                <asp:TextBox id="disksize" runat="server"/>
                        <asp:RegularExpressionValidator ID="RegularExpressionValidator1" runat="server"  ErrorMessage="Must Contain only Numbers" ControlToValidate="disksize" ValidationExpression="[0-9]*$"></asp:RegularExpressionValidator>
                <br /><br />    
       
                Purpose:
                <asp:TextBox id="purpose1" runat="server" />
                <br /><br />
        
                      
                 Operating System:
<!--This is data will be pulled from the database once connection has been made -->
                <asp:DropDownList ID="operatingsystem" runat="server" AutoPostBack="false">
                    <asp:ListItem> </asp:ListItem>
                    <asp:ListItem>Windows</asp:ListItem>
                    <asp:ListItem>OS2</asp:ListItem>
                    <asp:ListItem>OS3</asp:ListItem>
                </asp:DropDownList>
                <br /><br />

<!--Main submit button to send data to the database  -->
                <asp:Button id="submit1" Text="Submit" runat="server" OnClick="btnSave_Click" />




************************************************************************************************************
c# code behind this asp.net


using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;
using System.Data.SqlClient;

namespace WebApplication1
{
    public partial class _Default : Page
    {
       
        
        protected void Page_Load(object sender, EventArgs e)
        {          
        }

        // This is a way to extract the data from each textbox and ensure all boxes are filled. (Not in use at the moment using btnSave_Click to test database connection.)
        protected void Submission_form(object sender, EventArgs e)
        {


            var server_name5 = servername.Text; //  extracting the sting from the textbox
            var server_name6 = server_name5.Length; // getting the length

            var ip_address1 = ipaddress.Text;
            var ip_address2 = ip_address1.Length;

            var operating_system = operatingsystem.Text;
            var operating_system2 = operating_system.Length;

            var disk_size = disksize.Text;
            var disk_size2 = disk_size.Length;

            var purpose = purpose1.Text;
            var purpose_length = purpose.Length;

            // This if statement is running through each of the variale lengths to ensure that there is data entered
            if ((server_name6 > 0) && (ip_address2 > 0) && (operating_system2 > 0) && (disk_size2 > 0) && (purpose_length > 0)) 
                //submit1.Visible = true;
                Response.Write("Submission sent!"); // if all fields are filled



            else //submit1.Visible = false;
                Response.Write("Please fill in all the required fields"); // if there are filds without data




        }
        
        protected void btnSave_Click(object sender, EventArgs e) {


            var server_name7 = servername.Text;

            SqlConnection conn = new SqlConnection("Data Source=xia96a5ydl.database.windows.net; User Id=Emrul; Password=Password1; Initial Catalog=Server_Monitoring_Application"); conn.Open();

            SqlCommand cmd = new SqlCommand("INSERT INTO Serverinfo(Server_Name) values ('" + server_name7 + "')", conn); cmd.ExecuteNonQuery();
 

                                                                 }



    }

}
    

         
                      
            </div>
                <br>

</asp:Content>
