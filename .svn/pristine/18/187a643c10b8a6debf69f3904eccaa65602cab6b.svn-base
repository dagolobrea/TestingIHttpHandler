using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;

namespace TestingIHttpHandler
{
    public partial class _Default : System.Web.UI.Page
    {
        protected void Page_Load(object sender, EventArgs e)
        {
            Context.Items.Add("Content", "colum1;column2;column3");
            Context.Items.Add("FileType", ".csv");

            DownloadHandler handler = new DownloadHandler();
            Server.Transfer(handler, true);
        }
    }


    public class DownloadHandler : Page
    {
        public override void ProcessRequest(HttpContext context)
        {
            var content = context.Items["Content"].ToString();
            var fileType = context.Items["FileType"].ToString();
            var fileName = "CSV_" + DateTime.Now.ToString() + fileType;

            context.Response.ClearHeaders();
            context.Response.ClearContent();
            context.Response.Clear();
            context.Response.ContentType = "application/ms-excel";
            context.Response.AddHeader("content-disposition", "inline;filename=" + fileName);

            context.Response.Write(content);
            context.Response.End();

        }
    }
}
