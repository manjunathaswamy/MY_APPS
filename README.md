my_test
=======
package com.contactapp.test;

import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.util.Collection;
import java.util.LinkedList;
import java.util.Scanner;
import java.util.TreeSet;




public class ContactApp
{
  static BufferedReader br=null;
	static BufferedWriter bw=null;
	static Scanner sc1=new Scanner(System.in);
	static Scanner sc2=new Scanner(System.in);
	static Collection sort=new TreeSet();
	static Collection phoccur=new LinkedList();
	static Collection eoccr=new LinkedList();
	static Collection col=new LinkedList();
	static Collection ctctname=new LinkedList();
	static Collection dofb=new LinkedList();
	static Collection addrss=new LinkedList();
	static Collection emails =new LinkedList();
	static Collection phnnums=new LinkedList();
	static Collection tags=new LinkedList();
	static Collection cll=new LinkedList();
	static Collection ad=new LinkedList();
	static int ch=0;
	static int sel=0;
	static File f=null;
	static String currentline,strg;
	static String contactbookname,contactname,dob,addrs,email,phnnum,petname,tag,contacttype=null;

	
	public static void main(String[] args) throws IOException 
	{
		
		
		try
		{
		while(ch!=3)
		{
			System.out.println("Press 1 to Create Contacts Book");
			System.out.println("Press 2 to Load Contacts Book");
			System.out.println("Press 3 to Exit");
			System.out.println("Enter choice:");
			ch = sc1.nextInt();
			switch(ch)
			{
				case 1:
						
						System.out.println("Give conntact book name:");
						contactbookname = sc2.nextLine();
						if(col.contains(contactbookname))
							throw new IllegalArgumentException("contactbookname already exist give other name");
						else
						System.out.println(col.add(contactbookname));
						 f=new File(contactbookname);	
						 if(!f.exists())
						 {
							  f.createNewFile();
							  System.out.println("The absolute path of the file is: " +f.getAbsolutePath());
							  
						 }
						 else
							  throw new IllegalArgumentException("contactname.txt already present in current directory give other name ");
						 
						 		contactbook();
						 
						 break;
				case 2:
					System.out.println("load the contactbook name");
					String str=sc2.nextLine();
					File f1=new File(str);
					if(!f1.exists())
					{
						throw new IllegalArgumentException("nevu enter madida contact book not available");
					}
					
						contactbook();
					break;
				case 3:
					System.out.println(" tata bye bye ");
					System.exit(0);
				default:
					throw new IllegalArgumentException("hello !!!! give num b/w 1 to 3 only");
			}
	
		}
		}
		catch(Exception e)
		{
			e.printStackTrace();
		}
	}
	public static void contactbook() throws IOException
	{
		 while(sel!=6)
			{
				System.out.println("Press 1 to Add a Contacts Book");
				System.out.println("Press 2 to Edit a Contacts Book");
				System.out.println("Press 3 to Remove a Contacts Book");
				System.out.println("Press 4 to List the Contacts Book");
				System.out.println("Press 5 to Search Contacts Book");
				System.out.println("Press 6 to Go back");
				System.out.println("enter choice:");
				sel=sc1.nextInt();
				switch(sel)
				{
				case 1:
						System.out.println("give the contact name to add");
						contactname=sc2.nextLine();
						 strg=contactname;
						validate();
						
						if(ctctname.contains(contactname))
							throw new IllegalArgumentException("contactname already exist give other name");
						else
						ctctname.add(contactname);
						
						System.out.println("give the dateofbirth to add");
						dob=sc2.nextLine();
						strg=dob;
						validate();
						dofb.add(dob);
						
						System.out.println("give the addrs to add");
						addrs=sc2.nextLine();
						strg=addrs;
						validate();
						addrss.add(addrs);
						
						System.out.println("give the email to add");
						email=sc2.nextLine();
						strg=email;
						validate();
						if(!(email.contains("@")))
							throw new IllegalArgumentException("email id must contain @ Symbol");
						emails.add(email);
						
						System.out.println("give the phone num to add");
						phnnum=sc2.nextLine();
						strg=phnnum;
						validate();
						long z=0;
						try
						{
							z=Long.parseLong(phnnum);
							phnnums.add(phnnum);
						}
						catch(Exception e)
						{
							throw new IllegalArgumentException("Mr. dayavittu enter Digit only");
						}
						
						
						System.out.println("give the tag to add");
						tag=sc2.nextLine();
						strg=tag;
						validate();
						tags.add(tag);
						
						System.out.println("choose the contact type");
						System.out.println("press 1 if the contact type is family");
						System.out.println("press 2 if the contact type is friend");
						System.out.println("press 3 iif the contact type is colleauge");
						System.out.println("enter choice:");
					int choice=0;
					choice=sc1.nextInt();
					
						switch(choice)
						{
						case 1:
								System.out.println(contacttype="family");
								
								break;
						case 2:
								contacttype="friend";
								
								break;
						case 3: 
								contacttype="colleauge";
								
								break;
						default:
							throw new IllegalArgumentException ("namasthe dayvittu enter num b/w 1 to 3");
								
								
								
						}
						
					
					System.out.println(contactname=contactname+":"+tag+":"+dob+":"+addrs+":"+email+":"+phnnum+":"+contacttype);
					
					try 
			        {
					 	 bw=new BufferedWriter(new FileWriter(f,true));
					 	 bw.write(contactname);
					 	 bw.newLine();
			        } catch (IOException e)
			        {
			           e.printStackTrace() ;
			        } 
			        finally 
			        {
			        	
			            try
			            {
			            	if(bw!=null)
			                bw.close();
			            } catch (IOException e)
			            {
			                e.printStackTrace();
			            }
			        }
					break;

				case 2:
					
					
						System.out.println("enter 1 to change mail id");
						System.out.println("enter 2 to change phnnum");
						System.out.println("enter three to goback");
						System.out.println("enter your value:");
						
						int val=sc1.nextInt();
						switch(val)
						{
						case 1:
							BufferedReader br=null;
							System.out.println("enter your mial id to replace");
							CharSequence cs=null;
							cs=sc2.next();
							String stri=(String)cs;
							if(stri.contains("@"))
							{
							try
							{
								br=new BufferedReader(new FileReader(contactbookname));
								String currentline;
								Collection file=new LinkedList();
								while((currentline=br.readLine())!=null)
								{
									file.add(currentline);
								}
								System.out.println("enter your new email id to add");
								CharSequence st=sc2.next();
								String strin=(String) st;
								if(!(strin.contains("@")))
									throw new IllegalArgumentException("your id must contain @ symbol");
								int test=0;
								for(Object o:file)
								{
									String str=(String) o;
									
									
									if(str.contains(cs))
									{
										
										ad.add(str);
										System.out.println(str=str.replace(cs,st));
										cll.add(str);
										test++;
									}
								}
								System.out.println("");
								if(test<=0)
									throw new IllegalArgumentException("neevu enter madida email id not Exist in contactbook");
								file.removeAll(ad);
								file.addAll(cll);
								BufferedWriter wr=null;
									
									try
									{
										wr =new BufferedWriter(new FileWriter(contactbookname));
										for(Object x:file)
										{
											String s=(String) x;
											wr.write(s);
											wr.newLine();
											
										}
									}
									catch(IOException exe)
									{
										exe.printStackTrace();
									}
									finally
									{
										if(wr!=null)
											wr.close();
									}
							
								
							}
							catch(IOException ex)
							{
								ex.printStackTrace();
							}
							finally
							{
								try
								{
								if(br!=null)
									br.close();
								}
								catch(Exception e)
								{
									e.printStackTrace();
								}
							}
						
							break;
							}
							else
								throw new IllegalArgumentException("enter valid email id");
						case 2:
							BufferedReader Br=null;
							System.out.println("enter your phnnum to replace");
							CharSequence Cs=null;
							Cs=sc2.next();
							String sr=(String) Cs;
							long i=0;
							try
							{
								i=Long.parseLong(sr);
							}
							catch(Exception e)
							{
								throw new IllegalArgumentException("mr!..enter digit only");
							}
							{
							try
							{
								Br=new BufferedReader(new FileReader(contactbookname));
								
								Collection file=new LinkedList();
								while((currentline=Br.readLine())!=null)
								{
									file.add(currentline);
								}
								System.out.println("enter your phnnum  to add");
								CharSequence st=sc2.next();
								int test=0;
								for(Object o:file)
								{
									String str=(String) o;
									
								//	System.out.println(str.contains(Cs));
									if(str.contains(Cs))
									{
										
										ad.add(str);
										System.out.println(str=str.replace(Cs,st));
										
										cll.add(str);
										test++;
									}
								}
								System.out.println("");
								if(test<=0)
									throw new IllegalArgumentException("phone number not exist in contactbook");
								file.removeAll(ad);
								file.addAll(cll);
								BufferedWriter wr=null;
									
									try
									{
										wr =new BufferedWriter(new FileWriter(contactbookname));
										for(Object x:file)
										{
											String s=(String) x;
											wr.write(s);
											wr.newLine();
											
										}
									}
									catch(IOException exe)
									{
										exe.printStackTrace();
									}
									finally
									{
										try
										{
										if(wr!=null)
										wr.close();
										}
										catch(Exception e)
										{
										e.printStackTrace();
										}
									}
								
							}
							catch(Exception  ex)
							{
								ex.printStackTrace();
							}
							finally
							{
								try
								{
								if(Br!=null)
									Br.close();
								}
								catch(Exception ee)
								{
									ee.printStackTrace();
								}
							}
							
							break;
							}
							
						
						}
					
						
					break;
				case 3:
					System.out.println("enter the contact name which u like to remove");
					BufferedReader BR=null;
					CharSequence name=null;
					name=sc2.nextLine();
					{
					try
					{
						BR=new BufferedReader(new FileReader(contactbookname));
						String presentline;
						Collection rmv=new LinkedList();
						while((presentline=BR.readLine())!=null)
						{
							rmv.add(presentline);
						}
			
						Collection co=new LinkedList();
						int test=0;
						for(Object o:rmv)
						{
							String str=(String) o;
							
							
							if(str.contains(name))
							
							{
								ctctname.remove(str);
								co.add(str);
								test++;
							}
						}
						if(test<=0)
							throw new IllegalArgumentException("the contactname u enterd is not Exist");
						
						rmv.removeAll(co);
						BufferedWriter wr=null;
							
							try
							{
								wr =new BufferedWriter(new FileWriter(contactbookname));
								for(Object x:rmv)
								{
									String s=(String) x;
									wr.write(s);
									wr.newLine();
									
								}
							}
							catch(IOException exe)
							{
								exe.printStackTrace();
							}
							finally
							{
								try
								{
								if(wr!=null)
									wr.close();
								}
								catch(Exception ee)
								{
									ee.printStackTrace();
								}
							}
					
						
					}
					catch(IOException ex)
					{
						ex.printStackTrace();
					}
					finally
					{
						try
						{
						if(BR!=null)
							BR.close();
						}
						catch(Exception e)
						{
							e.printStackTrace();
						}
					}
					
					
					}
					break;
					
				case 4:
					System.out.println("press 1 to list contacts by alphabetical listing by name");
					System.out.println("Press 2 to list contacts by string length ");
					System.out.println("Press 3 to list contacts by alphabetical ordering of tags");
					int or=0;
					or=sc1.nextInt();
					switch(or)
					{
						case 1:
						
						try 
						{
							br=new BufferedReader(new FileReader(contactbookname));
						}
						catch (FileNotFoundException e1) {
							
							e1.printStackTrace();
						}
							
							try
							{
								while((currentline=br.readLine())!=null)
								{
									sort.add(currentline);
								}
								System.out.println(sort);
							}
								catch(Exception e)
								{
									e.printStackTrace();
								}
							finally
							{
								try
								{
									if(br!=null)
									br.close();
								}
								catch(Exception e)
								{
									e.printStackTrace();
								}
							}
						break;
							
							
						case 2:
						
							br=new BufferedReader(new FileReader(contactbookname));
							StrLengthComp sl=new StrLengthComp();
							 Collection sortlen=new TreeSet(sl);
							try
							{
								while((currentline=br.readLine())!=null)
								{
									sortlen.add(currentline);
								}
									System.out.println(sortlen);
							}
							catch(Exception e)
							{
									e.printStackTrace();
							}
							finally
							{
								if(br!=null)
									br.close();
							}
						break;
						case 3:
							br=new BufferedReader(new FileReader(contactbookname));
							Collection ll=new LinkedList();
							Collection tag=new TreeSet();
							Collection addtag=new LinkedList();
							try
							{
								while((currentline=br.readLine())!=null)
								{
									ll.add(currentline);
								}
							
								for(Object o:ll)
								{
									String ts=(String)o;
									String separator=":";
									int pos=ts.indexOf(separator);
									ts=ts.substring(pos+separator.length());
									tag.add(ts);
								}
								
								for(Object o:ll)
								{
									String tg=(String)o;
								
									for(Object q:tag)
									{
										String tsg=(String)q;
										
										if(tg.contains(tsg))
										{
											tg=tg.replace(tsg,tsg);
											addtag.add(tg);
										}
									}
								}
								System.out.println(addtag);
							}
							catch(Exception e)
							{
								e.printStackTrace();
							}
							finally
							{
								try
								{
									if(br!=null)
									br.close();
								}
								catch(Exception ee)
								{
									ee.printStackTrace();
								}
							}
							break;
							
					}
					break;
				case 5:
					System.out.println("enter the string to search in contact book");
					CharSequence sg=sc2.nextLine();
					int count=0;
					for(Object o:emails)
					{
						String str=(String)o;
						
						if(str.contains(sg))
						{
							
							count++;
							for(Object o1:ctctname)
							{
								String st=(String)o1;
								br=new BufferedReader(new FileReader(contactbookname));
								String currentline;
							
								while((currentline=br.readLine())!=null)
								{
									if(currentline.contains(str)&&currentline.contains(st))
									{
										eoccr.add(st+":"+str);
									}
								}
							}
						}
					}	
						
						System.out.println("");
						System.out.println("numof occurrence of email "+count);
						System.out.println("");
						for(Object e:eoccr)
						{
							String eo=(String)e;
							System.out.println(eo);
							System.out.println("");
						}
						int inc=0;
						for(Object o2:phnnums)
						{
							String si=(String)o2;
							if(si.contains(sg))
							{
								count++;
								inc++;
								for(Object o3:ctctname)
								{
									String sig=(String)o3;
									br=new BufferedReader(new FileReader(contactbookname));
									String currentline;
									
									while((currentline=br.readLine())!=null)
									{
										if(currentline.contains(sig)&&currentline.contains(si))
										{
											phoccur.add(sig+":"+si);
										}
									}
								}
							}
						}
							System.out.println("number of occurence in phonenum "+inc);
							
							for(Object e:phoccur)
							{
								String eo=(String)e;
								System.out.println(eo);
							}
							System.out.println("total number of occurence in phonenum "+count);
						
					
					case 6:
						String[] a={"",""};
						main(a);
						break;
						
					default:
						throw new IllegalArgumentException("maga u must enter num b/w 1 to 6 only");
				}
				
				
			}
		
	}
	public static void validate()
	{
		if(strg==null ||strg.trim().equals(""))
			throw new IllegalArgumentException("cant be blank or null");
	}

	
}
										 
