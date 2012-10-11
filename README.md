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
    

         
                      
            </div>
                <br>

</asp:Content>
