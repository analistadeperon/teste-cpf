# teste-cpf
cpf
// JavaScript Document
function FormataCpf(campo, teclapres)

			{
				var tecla = teclapres.keyCode;
				var vr = new String(campo.value);
				vr = vr.replace(".", "");
				vr = vr.replace("/", "");
				vr = vr.replace("-", "");
				tam = vr.length + 1;
				if (tecla != 14)
				{
					if (tam == 3)
						campo.value = vr.substr(0, 2) + '.';
					if (tam == 6)
						campo.value = vr.substr(0, 2) + '.' + vr.substr(2, 5) + '.';
					if (tam == 10)
						campo.value = vr.substr(0, 2) + '.' + vr.substr(2, 3) + '.' + vr.substr(6, 3) + '/';
					if (tam == 15)
						campo.value = vr.substr(0, 2) + '.' + vr.substr(2, 3) + '.' + vr.substr(6, 3) + '/' + vr.substr(9, 4) + '-' + vr.substr(13, 2);
				}
			}



function validarCpf(cpf) {
 
    cpf = cpf.replace(/[^\d]+/g,'');
 
    if(cpf == '') return false;
     
    if (cpf.length != 11)
        return false;
 
    // Elimina CNPJs invalidos conhecidos
    if (cpf == "00000000000000" || 
        cpf == "11111111111111" || 
        cpf == "22222222222222" || 
        cpf == "33333333333333" || 
        cpf == "44444444444444" || 
        cpf == "55555555555555" || 
        cpf == "66666666666666" || 
        cpf == "77777777777777" || 
        cpf == "88888888888888" || 
        cpf == "99999999999999")
        return false;
         
    // Valida DVs
    tamanho = cpf.length - 2
    numeros = cpf.substring(0,tamanho);
    digitos = cpf.substring(tamanho);
    soma = 0;
    pos = tamanho - 7;
    for (i = tamanho; i >= 1; i--) {
      soma += numeros.charAt(tamanho - i) * pos--;
      if (pos < 2)
            pos = 9;
    }
    resultado = soma % 11 < 2 ? 0 : 11 - soma % 11;
    if (resultado != digitos.charAt(0))
        return false;
         
    tamanho = tamanho + 1;
    numeros = cnpj.substring(0,tamanho);
    soma = 0;
    pos = tamanho - 7;
    for (i = tamanho; i >= 1; i--) {
      soma += numeros.charAt(tamanho - i) * pos--;
      if (pos < 2)
            pos = 9;
    }
    resultado = soma % 11 < 2 ? 0 : 11 - soma % 11;
    if (resultado != digitos.charAt(1))
          return false;
           
    return true;
    
}

 Array.unshift()input type="text" name="cpf" id="cpf" onkeyup="FormataCpf(this,event)" maxlength="11" 
