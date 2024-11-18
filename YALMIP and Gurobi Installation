% YALMIP and Gurobi setup
yalmip('clear');

% Define decision variables
x = sdpvar(1, 1);
y = sdpvar(1, 1);

% Objective function
objective = (x - 3)^2 + (y - 4)^2;

% Constraints
constraints = [x + 2*y <= 7, x >= 0, y >= 0];

% Solve the problem using Gurobi solver
options = sdpsettings('solver', 'gurobi', 'verbose', 1);
optimize(constraints, objective, options);

% Display results
x_opt = value(x);
y_opt = value(y);
obj_value = value(objective);

disp(['Optimal x: ', num2str(x_opt)]);
disp(['Optimal y: ', num2str(y_opt)]);
disp(['Objective value: ', num2str(obj_value)]);
