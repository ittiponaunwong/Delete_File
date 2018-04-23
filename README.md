# Delete_File
Delete a specific file from folder using C# .Net

                        try
                            {
                                //App.config => appSettings => <add key="path_file" value="\\web-t07.test.corp\AppTest\Project1\assets\form_log\pdf" />
                                string PATH = ConfigurationSettings.AppSettings["path_file"].ToString();
                                DateTime Time_delete = DateTime.Now.AddDays(-3);
                                DirectoryInfo directory = new DirectoryInfo(PATH);

                                //All Get File
                                //var files = directory.GetFiles().ToList(); 
                                var files = directory.GetFiles("*.html").ToList();

                                foreach (var item in files)
                                {
                                    string item_name = item.ToString(); //Name
                                    string get_date_file = item.CreationTime.ToString(); //Create Date
                                    string sourcePath = PATH + "/" + item_name; //Path Date

                                    DateTime Time_Create_file = DateTime.Parse(get_date_file);

                                    if (Time_Create_file <= Time_delete)
                                    {
                                        if (System.IO.File.Exists(sourcePath))
                                        {
                                            System.IO.File.Delete(sourcePath);
                                        }
                                    }
                                }
                            }
                            catch (Exception ex)
                            {
                                Message_data = ex.Message;
                            }
