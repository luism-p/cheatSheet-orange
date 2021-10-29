
**Input - Campo text**
~~~xhtml
<div class="col-md-3">
    <div class="vo-form__container">
        <aui:input type="text" name="[nombre]" 
                   label="[etiqueta]"
                   value="[Valor]" disabled="true" cssClass="clean">
            <aui:validator name="required"/>
        </aui:input>
    </div>
</div>
~~~

**Input - Campo textArea**

```xhtml
<div class="col-md-3">
    <div class="vo-form__container">
        <aui:input type="textarea" name="[nombre]" label='[etiqueta]'
                   rows="2" cols="20" maxLength="400" value="[valor]"/>
    </div>
</div>
```

**Input - Campo radioButton**

```xhtml
<!-- OJO: deben tener mismo nombre pero diferentes id, para capturar los eventos se debe usar el id-->
<div class="col-md-offset-1 col-md-11">
    <div class="form-group">
        <label class="vo-form__label" for="[nombre]">
            <liferay-ui:icon icon="asterisk" markupView="lexicon" cssClass="text-warning"/>
            <liferay-ui:message key="com.liferay.everis.orange.key"/>
        </label>
        <aui:input name="[nombre]" id='[id]' type="radio" value="[valor]"
        label="[etiqueta]"checked="[boolean]" disabled="[boolean]"/>

        <aui:input name="[nombre]" id='[id]' type="radio"value="[valor]"
        label="[etiqueta]"checked="[boolean]" disabled="$[boolean]"/>
    </div>
</div>


<script>
    // Este cript corrije el error que se produce al pulsar los radio button

$(function () {
    var checkExiste = setInterval(function () {
        if ($('#<portlet:namespace/>[id]').siblings('ins.iCheck-helper').length > 0) {
            //para los botones de los radio
            $('#<portlet:namespace/>[id]').siblings('ins.iCheck-helper').on('click', function () {
                <!-- TODO implement -->
            });

            $('#<portlet:namespace/>[id]').siblings('ins.iCheck-helper').on('click', function () {
                <!-- TODO implement -->

            });
            clearInterval(checkExiste);
        }
    }, 10);
}
</script>

<style type="text/css">
/* CSS para cuando se deshabilita */

div.vo-radiocustom.checked.disabled:before {
    content: '\e929';
    color: #cccccc;
}
</style>

```

**Input - Campo datePicker**

```xhtml
<!-- Esto se debe inicializar para que funcione-->
<!-- Se pueden deshabilitar los días a elegir, mirar flexplan productos > masterPostgrado -->

<div class="col-md-offset-1 col-md-3">
    <div class="vo-form__container">
        <label class="vo-form__label vo-form__help--container">
            <liferay-ui:message key="com.liferay.everis.orange.key"/>
            <liferay-ui:icon icon="asterisk" markupView="lexicon" cssClass="text-warning"/>
        </label>
        <div class="vo-datepicker__layer">
            <aui:input name="[nombre]" value="[valor]"
            cssClass="vo-inputdate" label="" disabled="[boolean]">
                <aui:validator name="custom" errorMessage="com.liferay.everis.orange.error.date">
                            function (val, fieldNode, ruleValue) {
                                return vo_validate.date(val);
                            }
                </aui:validator>
                <aui:validator name="required"/>
            </aui:input>
        </div>
    </div>
</div>

<script>
    // Inicializar datePicker
    $(function () {

        YUI().use('aui-datepicker', function (Y) {
            new Y.DatePicker({
                trigger: '.vo-inputdate',
                mask: '%d/%m/%Y',
                popover: {
                    zIndex: 9999
                }
            });
        });
    }
</script>
```
**Input - campo selector**
```xhtml
<div class="vo-form__container">  
	<div class="vo-select nacionalidad">  
		<aui:select name="[nombre]" class="form-control"  
		cssClass="vo-selectdrop selectpicker clean" disabled="true"  
		data-selectvalue="[valor]" label="[etiqueta]">  
  
		  <aui:option value="" disabled="[boolean]" selected="[boolean]">  
	          <liferay-ui:message key="com.everis.liferay.orange.control.externos.cambio.seleccionar"/>  
	      </aui:option>  
		  <aui:option value="[valor]" label="[etiqueta]"/>
  
            <aui:validator name="required"/>  
        </aui:select>  
    </div>  
</div>
```