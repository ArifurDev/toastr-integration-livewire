# Tostar

This setup ensures that your Laravel application can easily trigger Toastr notifications through Livewire events. Whether using Livewire v2 or v3, this guide covers the necessary steps to get Toastr notifications up and running in no time.

## Setup

1. **Include Toastr in your main layout:**

    ```html
    <!-- Include Toastr CSS -->
    <link href="https://cdnjs.cloudflare.com/ajax/libs/toastr.js/latest/toastr.min.css" rel="stylesheet">

    <!-- Include jQuery -->
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>

    <!-- Include Toastr JS -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/toastr.js/latest/toastr.min.js"></script>
    ```

2. **Configure Toastr options:**

    ```html
    <script>
        $(document).ready(function(){
            toastr.options = {
                "progressBar": true,
                "positionClass": "toast-top-right",

                // "closeButton": false,
                // "debug": false,
                // "newestOnTop": false,
                // "preventDuplicates": false,
                // "onclick": null,
                // "showDuration": "300",
                // "hideDuration": "1000",
                // "timeOut": "5000",
                // "extendedTimeOut": "1000",
                // "showEasing": "swing",
                // "hideEasing": "linear",
                // "showMethod": "fadeIn",
                // "hideMethod": "fadeOut"
            }
        });

        document.addEventListener("livewire:init", () => {
            Livewire.on("toast", (event) => {
                toastr[event.notify](event.message);
            });
        });
    </script>
    ```

3. **configure the Livewire component:**

    ```php
      //you can use livewire v2
      return $this->dispatchBrowserEvent('toast', message: 'Please try again!', notify:'error' );

      //you can use livewire v3
      return $this->dispatch('toast', message: 'Please try again!', notify:'error' );
      
    ```



