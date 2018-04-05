  $(document).ready(function() {
    
      document.addEventListener('touchstart', handleTouchStart, false);        
      document.addEventListener('touchmove', handleTouchMove, false);

      var xDown = null;                                                        
      var yDown = null;                                                        

      function handleTouchStart(evt) {                                         
        xDown = evt.touches[0].clientX;                                      
        yDown = evt.touches[0].clientY;                                      
      };                                                

      function handleTouchMove(evt) {
        if ( ! xDown || ! yDown ) {
          return;
        }

        var xUp = evt.touches[0].clientX;                                    
        var yUp = evt.touches[0].clientY;

        var xDiff = xDown - xUp;
        var yDiff = yDown - yUp;

        if ( Math.abs( xDiff ) > Math.abs( yDiff ) ) {/*most significant*/
          if ( xDiff > 0 ) {
            /* left swipe */
            $('#pCarousel').carousel('next');
            $('#lCarousel').carousel('next');
            //SelectionChanged();
          } else {
            /* right swipe */
            $('#pCarousel').carousel('prev');
            $('#lCarousel').carousel('prev');
            //SelectionChanged();
          }                     
        } else {
          if ( yDiff > 0 ) {
            /* up swipe */ 
          } else { 
            /* down swipe */
          }                                                                 
        }
        /* reset values */
        xDown = null;
        yDown = null;                                             
      };
      $('#lCarousel').on('slid.bs.carousel', function (e) {
        //console.log('slide event!');
        SelectionChanged();
      });
});
  
  $(document).ready(function() {
        $(".content.purebusiness").hide();
    $(".sun").on("mouseenter", function() {
        $(".content.purebusiness").show();
    $(".content.purebusiness").css('z-index','999');
    })
    $('.content.purebusiness').on("mouseleave", function() {
        $(".content.purebusiness").hide();
    });
});
