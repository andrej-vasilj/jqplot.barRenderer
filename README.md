jqplot.barRenderer
==================

Adding error bars to the jqplot bar renderer

USAGE:

use the bar renderer as usual but with the extra options that can be seen in the examples below.
 
the option named "errorData" defines an array of normalized min and max points. This means that it is up to you to calculate the magnitude of the error for yor data and also to normalize it to the value of your data point. An error value of 0.1 indicates 10% error.

the option named "errorTextData" allows you to specify labels for each of the error bars. In this way you can add stars for statistical significance so that they are displayed on top of the error bar.


EXAMPLE 1 (vertical bar chart):

    var s1 = [200, 600, 700, 1000];
    var s2 = [460, -210, 690, 820];
    var s3 = [-260, -440, 320, 200];
    
    var ticks = ['May', 'June', 'July', 'August'];
     
     //normalized error bar min/max values (0.1 indicates 10% of intensity)
    var errorS1 = [{min:0.1, max:0.3}, {min:0.1, max:0.3}, {min:0.1, max:0.3}, {min:0.1, max:0.3}];
    var errorS2 = [{min:0.2, max:0.4}, {min:0.2, max:0.4}, {min:0.2, max:0.4}, {min:0.2, max:0.4}];
    var errorS3 = [{min:0.3, max:0.5}, {min:0.3, max:0.5}, {min:0.3, max:0.5}, {min:0.3, max:0.5}];
    
    //error bar text (incase you want to provide statistical significance stars or some other kind of small labels)
    var errorTextS1 = ["*", "*", "*", "*"];
    var errorTextS2 = ["**", "**", "**", "**"];
    var errorTextS3 = ["***", "***", "***", "***"];

 var plot1 = $.jqplot('chart1', [s1, s2, s3], {
        seriesDefaults:{
            renderer:$.jqplot.BarRenderer,
            rendererOptions: {
                fillToZero: true,
                errorBarWidth: 2, //thickness of the error bars
                errorBarColor: "black", //color of the error bars
                errorBarTextFont: "bold 16px Arial", //error bar text font 
                errorData: [errorS1, errorS2, errorS3],
                errorTextData: [errorTextS1, errorTextS2, errorTextS3],
                barDirection: 'vertical'
            }
        },
        series:[
            {label:'Hotel'},
            {label:'Event Regristration'},
            {label:'Airfare'}
        ],
        axes: {
            xaxis: {
                renderer: $.jqplot.CategoryAxisRenderer,
                ticks: ticks
            }
        }
    });






EXAMPLE 2: horizontal bar chart

    var s1 = [[2,1], [4,2], [6,3], [3,4]];
    var s2 = [[5,1], [1,2], [3,3], [4,4]];
    var s3 = [[4,1], [7,2], [1,3], [2,4]];
     
     //normalized error bar min/max values (0.1 indicates 10% of intensity)
    var errorS1 = [{min:0.1, max:0.3}, {min:0.1, max:0.3}, {min:0.1, max:0.3}, {min:0.1, max:0.3}];
    var errorS2 = [{min:0.2, max:0.4}, {min:0.2, max:0.4}, {min:0.2, max:0.4}, {min:0.2, max:0.4}];
    var errorS3 = [{min:0.3, max:0.5}, {min:0.3, max:0.5}, {min:0.3, max:0.5}, {min:0.3, max:0.5}];
    
    //error bar text (incase you want to provide statistical significance stars or some other labels)
    var errorTextS1 = ["*", "*", "*", "*"];
    var errorTextS2 = ["**", "**", "**", "**"];
    var errorTextS3 = ["***", "***", "***", "***"];
    
    var plot1 = $.jqplot('chart1', [s1, s2, s3], {
        seriesDefaults:{
            renderer:$.jqplot.BarRenderer,
            rendererOptions: {
                fillToZero: true,
                errorBarWidth: 2, 
                errorBarColor: "black", 
                errorBarTextFont: "bold 16px Arial", 
                errorData: [errorS1, errorS2, errorS3],
                errorTextData: [errorTextS1, errorTextS2, errorTextS3],
                barDirection: 'horizontal'
            }
        }
    });
