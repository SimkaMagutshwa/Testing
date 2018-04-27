# Testing
Code to test the view of my application
<!DOCTYPE html>


<html>
<head>
    <meta name="viewport" content="width=device-width" />
    <title>@ViewBag.Title</title>
    @Styles.Render("~/Content/css")
    @Scripts.Render("~/bundles/modernizr")

</head>
<body>
    <div class="navbar navbar-default navbar-fixed-top" style="background-color:#428bca">
        <div class="container">
            <div class="navbar-header">
                <button type="button" class="navbar-toggle" data-toggle="collapse" data-target=".navbar-collapse">
                    <span class="icon-bar"></span>
                    <span class="icon-bar"></span>
                    <span class="icon-bar"></span>
                </button>
                @*@Html.ActionLink("Application name", "Index", "Home", new { area = "" }, new { @class = "navbar-brand" })*@
            </div>
            <div class="navbar-collapse collapse">
                <ul class="nav navbar-nav">
                    <li>@Html.ActionLink("Law Practice", "Index", "Home",new { style = "color:white" })</li>
                    @*<li>@Html.ActionLink("About", "About", "Home")</li>
                        <li>@Html.ActionLink("Contact", "Contact", "Home")</li>*@
                </ul>
                @Html.Partial("_LoginPartial")
            </div>
        </div>

    </div>
    <div class="secondary-nav">

        <ul class="nav navbar-nav navbar-center" id="id">
            <li><a href="~/Home/Index">Dashboard</a></li>
            @{
                UserControlLogic ucl = new UserControlLogic();
                Client clientl = ucl.getClient(User.Identity.Name);
                var path = clientl.AttorneyID;
            }
            <li>@Html.ActionLink("My Attorney", "MyAttorney", "Clients", new { id = @path},null)</li>
            @*<li><a href="">Cases</a></li>
            <li><a href="">Calender</a></li>
            <li><a href="">Documents</a></li>*@
        </ul>
    </div>
    <br /><br />
    <h2 style="margin-left:2em">@ViewBag.Title</h2>

    @*<div class="divpic">
            <img src="~/Content/img/default.jpg" alt="No Image" width="250" style="border-radius:100%"/>
            @*<input type="file" name="Change Profile Picture" id="file" />
        </div>*@




    <div class="container-fluid" style="margin-left:4em">

        <div class="row">
            <div class="col-sm-3" style="background-color:white;">
                <div class="mx-auto" style="width: 250px;">
                    <div class="panel panel-info">
                        <div class="panel-heading"><h4><strong>MY INFORMATION</strong></h4></div>
                        <div class="panel-body">
                            <div class="mx-auto" style="width: 200px;">
                                @using (Html.BeginForm("Edit", "Clients", FormMethod.Get))
                                {
                                    
                                        
                                      
                                            UserControlLogic uc = new UserControlLogic();
                                            Client client = uc.getClient(User.Identity.Name);
                                        

                               
                                    
                                    
                                    <div class="blist">
                                        <ul>
                                            <li class="btn btn-primary btn-block">

                                                <a style="background-color:white">@Html.ActionLink("Update Contacts", "PortalEdit", "Clients", new { id = @client.ID }, null)</a>
                                            </li>

                                            <li class="btn btn-primary btn-block">

                                                <a style="background-color:white">@Html.ActionLink("My Profile", "Portal", new { id = client.ID })</a>
                                            </li>
                                        </ul>
                                    </div>
                                        
                                                                          
                                    
                                        

                                }
                                @*<p><a class="btn btn-primary btn-block" href="~/Attorneys/Create" hreflang="">Register attorney &rarr;</a></p>
                                     <p><a class="btn btn-primary btn-block" href="~/Clients/Create" hreflang="">Register client &rarr; </a></p>
                                    <p><a class="btn btn-primary btn-block" href="~/Attorneys/Index" hreflang="">Attorneys &rarr;</a></p>*@
                            </div>
                        </div>
                    </div>
                </div>


                <div class="mx-auto" style="width: 250px;">
                    <div class="panel panel-info">
                        <div class="panel-heading">
                            <h4 class="panel-title"><strong> SUMMARY</strong></h4>
                        </div>
                        <div class="panel-body">

                            <div class="mx-auto" style="width: 200px;">
                                <div class="blist">
                                    <ul>
                                        <li class="btn btn-primary btn-block">
                                            <p>
                                                @{
                                                    UserControlLogic enyinto = new UserControlLogic();
                                                    Client c = enyinto.getClient(User.Identity.Name);
                                                    Account acc = enyinto.AccountSummary(c.ID);
                                                }
                                                @Html.ActionLink("View Account Summary", "AccountSummary", "Clients", new { id = acc.AccountID }, null) 
                                             
                                            </p>
                                        </li>
                                    </ul>
                                </div>
                                @*<p><a class="btn btn-primary btn-block" href="~/Accounts/Index" hreflang=""> Accounts summaries &rarr; </a></p>*@
                            </div>
                        </div>
                    </div>
                </div>



                @* <div class="mx-auto" style="width: 250px;">
                                <div class="panel panel-info">

                                    <div class="panel-heading">
                                        <h4 class="panel-title"><strong>MANAGE CLIENTS</strong> </h4>
                                    </div>
                                    <div class="panel-body">
                                        <div class="mx-auto" style="width: 200px;">
                                            <p><a class="btn btn-primary btn-block" href="~/Clients/Create" hreflang="">Register client &rarr; </a></p>
                                            <p><a class="btn btn-primary btn-block" href="~/Clients/Index" hreflang="">Clients &rarr;</a></p>

                                            @Html.TextBox("search")
                                        <p><a class="btn btn-primary btn-block">Search&rarr;</a></p>
                                </div>
                            </div>
                        </div>
                    </div>*@


                <!--<p>Lorem ipsum...</p>-->
            </div>
            <div class="col-sm-9" height="420" style="background-color:white;">
                @RenderBody()
                <!---<p>Sed ut perspiciatis...</p>-->
            </div>
        </div>
    </div>

    @Scripts.Render("~/bundles/jquery")
    @Scripts.Render("~/bundles/bootstrap")
    @RenderSection("scripts", required: false)

</body>
</html>
