# awesome-angular-libs
### (My) Prerequisites:
- Usable by browserify style require()'s.
- Installable over NPM.

### Workflow:
- Install over NPM. `npm install cool-library --save-dev`
- Require into app as a dependency. `require('cool-library')`
- (Optional config step, per library)
- Use in controllers/directives as desired.


### Libraries:

##### - moment.js style date and time manipulation
`angular-moment` from https://github.com/urish/angular-moment.

1. npm install angular-moment
2. require('angular-moment')
3. Use:
 
`<span am-time-ago="order.created_at"></span>`

`{{order.delivery_time | amFromUnix | amDateFormat:'h:mm a'}}`

##### - bootstrap style modals, and other packages from bootstrap.js
`angular-ui-bootstrap` from https://github.com/angular-ui/bootstrap.

1. npm install angular-ui-bootstrap
2. require('angular-ui-bootstrap')
3. Use:
(controller which will spawn the modal)

```
controller: ['$scope', '$uibModal', function($scope, $uibModal){
                    $scope.openPopout = function(order){
                        var modal = $uibModal.open({
                            animation: false,
                            templateUrl: "src/directives/orderPopout/orderPopout.html",
                            controller: ['$scope', '$uibModalInstance', function($scope, $uibModalInstance){
                                $scope.order = order;
                                $scope.close = function(){
                                    $uibModalInstance.dismiss('cancel');
                                }
                            }]
                        })
                    }
```

(Finally, Set up a close button in orderPopout.html with `ng-click="close()"`)
