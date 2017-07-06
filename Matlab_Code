% Written by: @MajidAlaeina
% https://github.com/MajidAlaeinia


% A text to test the result: wabba_wabba_wabba_wabba_woo_woo_woo
clc; clear;
input = {'Enter your text here:'};
dlg_title = 'LZW Enc.'; % Title of the input window.
num_lines = 5; % Note: The text should be entered in one row. No "Shift+Enter" or "Enter" is allowed to seperate lines.
defaultoriginalText = {'Note: No "Enter" or "Shift+Enter" is allowed to seperate lines. Now you can delete these lines and Enter your text instead.'}; % Default Text in the text field entry.
options.Resize='on'; % Makes the prompt window resizable.
options.WindowStyle='normal'; % Makes the prompt window "normal" instead of being "modal".
originalText = inputdlg(input, dlg_title, num_lines, defaultoriginalText,options); % Displays the prompt window with assigned features.
originalText = cell2mat(originalText); % Makes the "originalText" a char class variable from cell class.
if isempty(originalText) % Nothing happens if the user clicks "Cancel" or clicks "Ok" while the text field is empty.
	return;
end
tic; % Starts measuring the elapsed time of the running code.
initialDictionary = unique(originalText); % Chooses the unique characters of the input text.
fprintf('Original Text:%s\n', originalText); % Displays the original text.
fprintf('Initial Dictionary:%s\n', initialDictionary); % Displays the initial dictionary.
for c = 1 : length(initialDictionary) % This loop counts the number of iterations of each unique character of the input text.
	countForThisChar = sum(originalText == initialDictionary(c));
	fprintf(2,'Number of iterations of character %s : %d\n', initialDictionary(c), countForThisChar); % Displays number of iteratios in red color.
end


Dictionary = cell(length(initialDictionary),1);
for j=1:length(initialDictionary)
    Dictionary(j) = {initialDictionary(j)};
end

P = '';
P_code = -1;
k = 0;

for i=1:length(originalText)
    Q = strcat(P,originalText(i));
    for j=1:length(initialDictionary)
        Q_code = 0;
        if (strcmp(Q, Dictionary(j)) == 1)
            Q_code = j;
            break;
        end
    end
    if (Q_code > 0)
        P = Q;
        P_code = Q_code;
    else
        k = k+1;
        output(k) = P_code;
        length(initialDictionary) = length(initialDictionary) + 1;
        Dictionary(length(initialDictionary)) = {Q};
        P = originalText(i);
        P_code = strfind(initialDictionary, P);
    end
end
k = k+1;
output(k) = P_code;
display(output);
toc; % Ends measuring the elapsed time of the running code.
