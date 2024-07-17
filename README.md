tbl_fiyat.Clear();
            DataRow bildr = tbl_fiyat.CreateRow();
		    
	        var bilcon = CreateServerConnection();   
            bilcon.Open();                                     
            var bilqry = new eBAIntegrationQuery("ServisBilgileri"); 
            bilqry.Parameters.Add("Belge No", lstbironcekiform.Value);  
            DataTable bildt = bilqry.Execute(bilcon);  
            bilcon.Close();  
              
            if (bildt.Rows.Count > 0)  
            { 
               foreach(DataRow bildr1 in bildt.Rows)
               {                      
                    bildr["txtguzergah"]=bildr1["txtguzergah"].ToString(); 
                    bildr["txtkm"]=bildr1["txtkm"].ToString();
                    bildr["lstaraclar"]=bildr1["lstaraclar"].ToString();
                    bildr["txt_maliyet"]=bildr1["txt_maliyet"].ToString();
                    tbl_fiyat.InsertRow(bildr);	
               }                          
            } 
