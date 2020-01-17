# Bootstrap Popover
Bootstrap Popover

Developing a Popover using the Bootstrap framework on .net
This popover will appear by pointing to Link

needs:
1) Bootstrap
2) Jquery
3) .net


In the html page:

<pre>
@section Scripts {   

    <script type="text/javascript">
        
        // This needed so it works after Ajax call
        $(document).ajaxComplete(function () {

            $('[data-toggle="popoverfull"]').popover({
                container: 'body',
                placement: 'right',
                trigger: 'click',
                html: true,
                title: function () {
                    return 'Items' +
                        '<button type="button" id="close" class="close" onclick="$(this).parent().parent().hide()">&times;</button>';
                },
                animation: false,
                content: function () {
                    var theValue = $(this).attr('value');                    
                    return $.ajax({
                        url: '/controllername/actionname?id=' + theValue,
                        dataType: 'html',
                        async: false
                    }).responseText;                    
                }
            });
        });

        $('[data-toggle="popoverfull"]').popover({
            container: 'body',
            placement: 'right',
            trigger: 'click',
            html: true,
            title: function () {
                return 'Items' +
                    '<button type="button" id="close" class="close" onclick="$(this).parent().parent().hide()">&times;</button>'
                    ;
            },
            animation: false,
            content: function () {
                var theValue = $(this).attr('value');                
                return $.ajax({
                    url: '/controllername/actionname?id=' + theValue,
                    dataType: 'html',
                    async: false
                }).responseText;
            }
        });
        
        $('.popover').click(function () {            
            $(this).popover('toggle');
        });

    </script>   
}

<style>
    .popover {
        width: 500px !important;
        max-width: 500px !important;
    }
</style>

<td style="font-size:10px;">                    
                        <u style="padding-left:5px" data-toggle=popoverfull value="XXXXX">XXXXX</u> 
</td>      

---------------------------------------------------------------------------------------

in the Controller / Action

public string actionname(string id)
        {    
            var stringreturned = "";           
            stringreturned += "<div style=font-size:x-small;><a href=https://XXXXX/?String=XXXXXX target=_blank>XXXX</a></div>";   
            return stringreturned;
        }
</pre>
