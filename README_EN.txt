# Nesca24D87
Nesca v24D87-801 (without backdoor)

Nesca - a network bot for searching for non-indexed resources on the Internet.
===============================================================



How to use DNS mode.
------------------------------

The order of characters is important. In the expression [XY], X must have a position in the" symbol table " less than the position of Y.
Example:
[az] - [OK]
[0b] - [OK]
[z-] - [OK]

[z0] - [FAIL]
[-g] - [FAIL]
[g6] - [FAIL]

"Character Table":
[
'0', '1', '2', '3', '4', '5', '6', '7', '8', '9', 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z', '_', '-'
]

Example:
mask: [09][09][09][09] TLD: .narod.ru -- will scan:		0000.narod.ru
								0001.narod.ru
								0002.narod.ru
								.....	 
								9998.narod.ru
								9999.narod.ru


mask: [az][az][az][az] TLD: .narod.ru -- will scan:		aaaa.narod.ru
								aaab.narod.ru
								aaac.narod.ru
								.....	 
								zzzy.narod.ru
								zzzz.narod.ru
															
															
mask: [0-][0-][0-][0-] TLD: .narod.ru -- will scan all possible names like 	4:0000.narod.ru
										0001.narod.ru
										0002.narod.ru
										.....	 
										aaa1.narod.ru
										aaa2.narod.ru
										.....	 
										zzzz1.narod.ru
										zzzz2.narod.ru
										.....	 
										---z.narod.ru
										---_.narod.ru
										----.narod.ru
																						
The length can controlled by number of expressions:
[0-] 						- all the names length 1;
[0-][0-] 					- all the names length 2;
[0-][0-][0-][0-][0-][0-] 			- all the names length 6;
						  and etc.

Also you can specify fixed parts of names:
lolka[09]zazka[0z] .mobi - will scan:		lolka0zazka0.mobi
						lolka0zazka1.mobi
						lolka0zazka2.mobi
						.....		
						lolka1zazka0.mobi
						lolka1zazka1.mobi
						lolka1zazka2.mobi
						.....		
						lolka9zazkax.mobi
						lolka9zazkay.mobi
						lolka9zazkaz.mobi
				
        
        
------------------------------
How to use Import mode.
------------------------------
										
А точнее, какой формат файла.
Example:
1.(Default)		127.0.0.1-127.0.0.255
			127.0.1.1-127.0.255.255
			127.1.1.1-127.255.255.255
			and etc.
	
2.(CIDR)		127.0.0.1/8
			127.0.0.1/16
			127.0.0.1/32
			and etc.
				
2.(Mixed)		127.0.0.1-127.0.0.255
			127.0.0.1/16
			127.0.0.1/32
			127.1.1.1-127.255.255.255
			and etc.
				
Also you can live the comments in file (You need to use # before comment):			#fool's ips
												127.0.0.1-127.0.0.255
												127.0.0.1/16
												#The Pentagon
												156.0.0.1/32
												157.0.0.1/16
