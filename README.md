# paging-in-c-using-two-button
OleDbConnection con;         OleDbCommand com;         DataSet ds;         OleDbDataAdapter da;         int maxnum = 0;         int maxvalue=6;         int minv = 0;         DataTable dt;         string strnametext;    public void binddata()     {         dt = new DataTable();         DataTable totalrecord = new DataTable();         string str = "select Code,Designation from Desig";         clsconnection connection = new clsconnection();         connection.GetConnect();         da = new OleDbDataAdapter(str, con);         con.Open();         da.Fill(minv,maxvalue,dt);         dataGridView1.DataSource = dt;         con.Close();     }   private void button4_Click(object sender, EventArgs e)        {           binddata();        }        private void button5_Click(object sender, EventArgs e)        {           // int next = minv + dt1.Rows.Count;            int nt = minv + dt.Rows.Count;            //ds = new DataSet();            dt = new DataTable();            da.Fill(nt, maxvalue, dt);            dataGridView1.DataSource = dt;            minv = nt;            if (dt.Rows.Count == maxvalue)            {                button5.Enabled = true;                button6.Enabled = true;            }            else            {                button5.Enabled = false;                button6.Enabled = true;                minv = nt + dt.Rows.Count;            }        }        private void button6_Click(object sender, EventArgs e)        {           //Int32 rc = dataGridView1.DisplayedRowCount(true);           int prev = (minv - dt.Rows.Count) &lt; (maxvalue) ? 0 : (minv - dt.Rows.Count);          // int prev = (maxvalue - minv) &lt; (maxvalue >= rc ? rc : maxvalue) ? 0 : (minv - rc);            dt = new DataTable();            da.Fill(prev, maxvalue, dt);            dataGridView1.DataSource = dt;            minv = prev;            if (minv == 0)            {                button5.Enabled = true;                button6.Enabled = false;            }            else            {                button5.Enabled = true;                button6.Enabled = true;            }        }a
