airbank-csv-export
==================

CVS Export bookmarklet pro Airbank internet bakovnictví

## Použití

1. Klikněte na spodní odkaz "Airbank - CSV Export" prvým tlačítkem myši a zvolte volbu "Přidat do záložek". 
   [Airbank - CSV Export](javascript:(function()%7Bvar%20separator%20%3D%20'%3B'%3Bvar%20total%20%3D%20parseInt(%24('%23grid-paging%20.cmpInline').text().trim().replace('%5C%2F%20'%2C%20''))%3Bvar%20lines%20%3D%20%5B%5B%22Proveden%C3%AD%22%2C%22%C3%9A%C4%8Det%22%2C%22Popis%22%2C%22Typ%22%2C%22%C4%8C%C3%A1stka%22%2C%22Poplatek%22%5D.join(separator)%5D%3Bfunction%20rows_to_lines()%20%7B%24('.mhtTable.mhtTableLinks%20tr').each(function(k%2C%20row)%20%7Bvar%20tds%20%3D%20%24(row).find('td')%3Blines.push(%5B%24(tds%5B1%5D).text().trim()%2C%24.map(%24(tds%5B2%5D).find('strong')%2C%20function(val)%20%7Breturn%20%24(val).text().trim()%3B%7D).join(%22%20-%20%22)%2C%24(tds%5B2%5D).find('.uiEllipsis').text().trim()%2C%24(tds%5B3%5D).text().trim()%2C%24(tds%5B4%5D).text().trim().replace(%22CZK%22%2C%20%22%22).replace(%22%2C%22%2C%20%22.%22)%2C%24(tds%5B5%5D).text().trim().replace(%22CZK%22%2C%20%22%22).replace(%22%2C%22%2C%20%22.%22)%5D.join(separator))%3B%7D)%3B%7Dfunction%20check_next(to_check%2C%20finished)%20%7Bif%20(!%24('body.mhtLoaderBodySync').length)%20%7Bvar%20curr%20%3D%20parseInt(%24('%23grid-paging%20input%5Btype%3Dtext%5D').val())%3Brows_to_lines()%3Bif%20(curr%20!%3D%20total)%20%7Bvar%20next%20%3D%20%24('.cmpLinkNext%20a')%3Bif(next)%20%7Bnext.click()%3B%7Dcheck_next(curr%20%2B%201%2C%20finished)%3B%7D%20else%20%7Bfinished()%3B%7Dreturn%3B%7DsetTimeout(function()%20%7Bcheck_next(to_check%2C%20finished)%3B%7D%2C%201000)%3B%7D%24('%23grid-paging%20input%5Btype%3Dtext%5D').val(1).blur()%3BsetTimeout(function()%20%7Bcheck_next(1%2C%20function()%20%7B%24('%3Cdiv%20class%3D%22cmpDialogInner%22%3E%3Cdiv%20class%3D%22cmpDialogCont%22%3E%3Cdiv%20class%3D%22cmpDialogPad%20clearfix%22%3E%3Cp%3E%3Ca%20href%3D%22%22%20download%3D%22export.csv%22%20class%3D%22csv%22%3E%3Cspan%20class%3D%22m2-icon-file%22%3E%3Cspan%20class%3D%22ui-button-icon%22%3E%3C%2Fspan%3E%3C%2Fspan%3ESt%C3%A1hnout%20soubor%3C%2Fa%3E%3C%2Fp%3E%3Cdiv%20class%3D%22mhtDialogCloseCallback%22%3E%3C%2Fdiv%3E%3C%2Fdiv%3E').dialog(%7B'title'%3A%20'Export'%2C'modal'%3A%20true%2C%7D)%3B%24('.csv').off('click').attr('href'%2C%20'data%3Aapplication%2Fcsv%3Bcharset%3Dutf-8%2C'%20%2B%20encodeURIComponent(lines.join(%22%5Cn%22)))%3B%7D)%3B%7D%2C%201000)%7D)())
2. Jděte do internetového bankovnictví, na stránku historie. Poté klikněte ve svých záložkách na položku "Airbank - CSV Export". Stránka by měla chvilku pracovat. Pokud máte vícero stránek, měl by se zobrazit i loader. Na konci vyskočí okénko s odkazem na CSV soubor.


## Co dělat, když nevěřím bookmarkletu. 

1. Nainstalujte si firebug for prohlížeče firefox. 
2. Spusťte konzoli - F12.
3. Vložte obsah souboru source.js a zmáčkněte ENTER
   nebo
   si udělejte vlastní bookmarklet pomocí (http://mrcoles.com/bookmarklet/).